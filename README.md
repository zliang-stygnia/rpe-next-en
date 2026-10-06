# Re:PhiEdit Next

Author：**cmdysj** “This project is a reconstruction of the original **Re:PhiEdit (RPE)** project, carried out with the use of **AI (GPT)**. Serves as an unofficial charting program for Phigros

[在线使用](https://kclg-ysj.github.io/rpe-next/) · [源码](https://github.com/kclg-YSJ/rpe-next)

Current Ver.：**0.7.1**。

Based on Canvas, Web Audio, WebGL, and IndexedDB. Supports note and event editing, real-time preview, shaders, multi-chart management, importing original RPE chart, and hotkey and transferable settings. It's still under developmnt and isn't guaranteed to be completely consistent with the original RPE; it is recommended to keep backups of your charts.

## Usage

It's recommend using the latest version of Edge or Chrome with hardware acceleration enabled. You can open online pages without installation

- In the chart library, select "Open JSON / PEZ" to import charts or create a new chart to import music, and illustration at the same time
- When migrating from the old RPE, select the original RPE source folder containing `Resources`, `Hotkey.txt`, and `Settings.json`. The transfer will read the original files and copy them to the current browser's chart library; it will prompt you before overwriting items with the same identifier name, and `extra.json` will be migrated along with the resources.
- Select a chart to enter edit mode. By default, Q/W/E/R keys are used for Tap/Drag/Flick/Hold, and spacebar is used to pause or resume. Hotkeys can be changed in the settings.
- After saving to the chart library, you can export a PEZ backup of the complete resources; Exporting with JSON does not include music and chart illustrations
- Shaders only affect the preview area. Overlapping events are applied based on line order, including shaders of the same type.
- Multi-select automatically opens multi-note/multi-event editing, with support for scripts, parameter history, and named presets. Events support cloning, batch splitting, and merging. When cloning, you can choose whether to keep the source events. Undo/redo preserves the corresponding multi-selection state

## How to run locally

Install Node.js version 22 or later, download the source code, and run this in the project directory:

```sh
npm start
```

On Windows, you can also double-click `start.cmd`. No npm dependency needs to be installed. It opens `http://127.0.0.1:4173` by default; closing the terminal will stop the localhost.

## Windows desktop-beta

The desktop package includes a built-in Electron runtime. After extracting it, double-click `RePhiEdit-Next.exe`; there is no need to install Node.js or a browser separately. Please keep the entire folder intact. A Windows x64 version is currently provided, and it has not been code-signed yet.

Desktop charts, configurations, and automatic backups are stored in `%APPDATA%\rpe-next-desktop`, independent from the web-based chart library; projects can be imported or migrated from the original RPE folder via PEZ.

Large textures are decoded on demand, and the cache resolution is selected based on the current display scale. When zooming in, a higher-resolution version is automatically added to the cache. This cache does not change the texture coordinates, logical dimensions, or the original exported assets.

Run manually only when a desktop package is needed (it will not be generated automatically as part of the web build or deployment):

```sh
npm ci
npm run build:desktop
```

The build output is located in `release/` and contains only the program, bundled assets, and license files; it does not include personal charts or development records. For development and debugging, you can run `npm run desktop`.

## Data & Privacy

Charts, media, hotkeys, settings, and automatic backups are stored in the current browser's local storage. The application does not have a server for uploading charts or any analytics/tracking. GitHub Pages provides static web hosting, and the hosting provider may record standard access logs when the website is visited.

Chart libraries are independent between different browsers, addresses, ports, and online/local versions. Clearing website data may delete your chart library and automatic backups, so export your PEZ files regularly. Selecting the original RPE folder is only used to read and transfer files locally; files will not be uploaded automatically.

## dev

```sh
npm test
npm run build
npm run smoke-build
npm run build:pages
```

`build` generates a locally runnable `dist/`; `build:pages` only generates the static page. After pushing to `main`, GitHub Actions automatically runs tests and deploys GitHub Pages.

## Licensing and Attribution

This project is licensed under [PolyForm Noncommercial 1.0.0](LICENSE), which permits only non-commercial use that complies with its terms; commercial use requires separate authorization. It is a source-available license, not an open-source license as defined by the OSI. Redistribution must retain the license and the required notices in [NOTICE](NOTICE).

The original RPE code and assets form the basis of this reconstruction, and their attribution and applicable rights are retained; the original rights and licenses of independent third-party content are not changed by this project's license. This project is not an official Phigros product.
