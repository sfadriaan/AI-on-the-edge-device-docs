# Documentation for the AI on the Edge Device Project

Go to https://jomjol.github.io/AI-on-the-edge-device-docs to use it.
 
This repo contains the documentation for the [AI-on-the-Edge-Device Project](https://github.com/jomjol/AI-on-the-edge-device).

# How does it work
1. You can edit any `*.md` document in the [docs](docs) folder.
1. Then create a Pull Request for it to merge it into the `main` branch (or edit it directly in the `main` branch if you have the required rights).
1. When it got merged, the [Github Actions](https://github.com/jomjol/AI-on-the-edge-device-docs/actions) will re-generate the documentation and place it in the `gh-pages` branch. This branch automatically gets populated to the public [Documentation Site](https://jomjol.github.io/AI-on-the-edge-device-docs)

## Editing a page
Each page has a link on its top-right corner `Edit on GitHub` which brings you directly to the Github editor.

## Adding new pages
1. Add a new `*.md` document in the [docs](docs) folder.
1. Add the **filename** to the [docs/nav.yml](docs/nav.yml) at the wished position in the **Links** section.

## Parameter Documentation
Each parameter in the [main project repo](https://github.com/jomjol/AI-on-the-edge-device) is documented in a separate file, see https://github.com/jomjol/AI-on-the-edge-device/tree/main/param-docs. The script in `param-docs/concat-parameter-pages.py` collects them and compiles it into the documentation as provided in https://jomjol.github.io/AI-on-the-edge-device-docs/Parameters.
The script should be run whenever one of the pages changed.
This happens automatically daily in the Github action.
if you run it manually, make sure to clone the main repo first, eg. using:
```bash
cd param-docs
rm -rf AI-on-the-edge-device
git clone https://github.com/jomjol/AI-on-the-edge-device.git
python concat-parameter-pages.py
cd ..
```

### Template Generator
The script `generate-template-param-doc-pages.py` should be run whenever a new parameter gets added to the config file.
It then checks if there is already page for each of the parameters.
 - If no page exists yet, a templated page gets generated.
 - Existing pages do not get modified.

If the parameter is listed in `expert-params.txt`, an **Expert warning** will be shown.

If the parameter is listed in `hidden-in-ui.txt`, a **Note**  will be shown.

## Formating
### Boxes
Boxes can be shown using the **admonition** extension.
```
!!! Note
    I am a note
```
Make sure to have 4-whitespace Intents!
Possible types: `attention, caution, danger, error, hint, important, note, tip, and warning`
See https://python-markdown.github.io/extensions/admonition/

## Local Test
To test it locally:
1. Clone this repo
1. Install the required tools (See also [.github/workflows/build-docs.yaml](.github/workflows/build-docs.yaml)):
    ```
    pip install --upgrade pip
    pip install mkdocs mkdocs-gen-files mkdocs-awesome-pages-plugin mkdocs-material pymdown-extensions mkdocs-enumerate-headings-plugin
    ```
1. In the main folder of the repo, call `mkdocs serve` (and keep it running).
  This will locally generate the documentation.
  You can access it under http://127.0.0.1:8000/AI-on-the-edge-device-docs/

    Any change to the files will automatically be applied.
