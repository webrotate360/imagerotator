# Overview

WebRotate 360 Product Viewer is an advanced solution for publishing highly interactive 360 product views, 3D product spins and the variety of e-commerce, e-learning and other knowledge base material. Find more details on our [core product page](https://www.webrotate360.com/products/webrotate-360-product-viewer.aspx) or in this [user guide](https://webrotate360.s3.amazonaws.com/sites/webrotate360/downloads/Resources/Readme.pdf).

This repo is available for users who need to integrate webrotate's 360 viewer runtime (i.e. browser based scripts or "imagerotator") in the modular builds of their websites and web apps.

## Examples

https://www.webrotate360.com/examples/browse-all-examples.aspx

## Installation

```sh
npm install @webrotate360/imagerotator --save
```

## Usage

1 . Require imagerotator after installation:
```js
import WR360 from '@webrotate360/imagerotator';
```
2 . Require viewer themes or an individual theme, e.g. thin.css, round.css, etc. (located under build/css):
```js
import '@webrotate360/imagerotator/build/css/all.css';
```
3 . Add container element with some id:
```html
<div id="webrotate360">
</div>
```
4 . There are two folders under **resources** in the root of the repo that you can copy to your website root for a quick test:
- **example** contains a test 360 product view.
- **graphics** contains default hotspot indicator SVG images.

5 . Initialize and run (e.g. in React's componentDidMount):
```js
const viewer = WR360.ImageRotator.Create('webrotate360');

viewer.licenseCode = 'your-license-code';
viewer.settings.configFileURL = '/example/example.xml';
viewer.settings.graphicsPath = '/graphics';
viewer.settings.alt = 'Your alt image description';
viewer.settings.responsiveBaseWidth = 800;
viewer.settings.responsiveMinHeight = 300;

viewer.settings.apiReadyCallback = (api, isFullScreen) => {
    this.viewerApi = api;
    this.viewerApi.images.onDrag(event => {
        console.log(`${ event.action }; current image index = ${ this.viewerApi.images.getCurrentImageIndex() }`);
    });
}

viewer.runImageRotator();
```
6 . Destroy viewer instance when not needed (e.g. in React's componentWillUnmount):
```js
if (this.viewerApi)
    this.viewerApi.delete();
```
Updated examples for React, Vue and Next are available [here](https://github.com/webrotate360).

## Documentation

Review API and Extended API sections in the [user guide](https://webrotate360.s3.amazonaws.com/sites/webrotate360/downloads/Resources/Readme.pdf). Alternatively, browse through these [integration templates](https://webrotate360.s3.amazonaws.com/sites/webrotate360/downloads/Resources/IntegrationTemplates.zip) (e.g. template_api.html).

## License

See license in EULA.pdf

