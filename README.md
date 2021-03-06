# Typescript Google Maps [![Build Status Master](https://travis-ci.org/DominikAngerer/typescript-google-maps.svg?branch=master)](https://travis-ci.org/DominikAngerer/typescript-google-maps)
[![TS-Google-Map Header (PNG)](http://ts-google-map.dominikangerer.com/github-images/header.png?v=1)](http://ts-google-map.dominikangerer.com/)

Wrote a simple Google Maps Component using Typescript and thought about sharing it with the community.

## [Documentation](http://ts-google-map.dominikangerer.com/docs/)

## [Running Example](http://ts-google-map.dominikangerer.com/)

[![TS-Google-Map Example (PNG)](http://ts-google-map.dominikangerer.com/github-images/example.png?v=2)](http://ts-google-map.dominikangerer.com/)

## Features:
- Default Google Maps 
- SnazzyMap Support (simply replace your SnazzyMap with the one I configured in the `SnazzyMaps.ts`)
- Default Center Object
- Free Geo IP Location (10.000 Request per Hour)
- New Default Icon `/images/icon.png`
- New Default Icon as .PSD `/images/icon.psd`
- No jQuery Needed
- Generated Test Data from [Json-Generator.com](http://beta.json-generator.com/Ey5gAmsMW)
- InfoBox JS Plugin
- Infobox Example
- Template example for InfoBoxes
- Full bower support
- MarkerClusterer JS Plugin Support
- MarkerClusterer Example

## Getting Started

To install this project
```
git clone git@github.com:DominikAngerer/typescript-google-maps.git typescript-google-maps
```

Now run:
```
npm install && bower install
```

## Run the server
```
gulp
```

## Build
To build, run
```
gulp build
```
If you add the `--production` flag all your js, css, html files get minified/uglified:
```
gulp build --production
```

## How to use

The Google Maps Component is splitted into 2 parts. 1. `data-google-map-component` is the part of the component on which the Controller Instance will be binded at. The 2. `data-google-map-canvas` will be the actual google map. This could than look like:

```
<div data-google-map-component>
    <div data-google-map-canvas style="height:90vh">
    </div>
</div>
```

Why split those 2 and not set it directly on one div? If you want to add something like a filter or input you can simply use it in the scope of the `data-google-map-component` without touching the `data-google-map-canvas` at all.

## Infobox Support

Google Maps has the `google.maps.OverlayView` but to use it in an easier way I've added the [InfoBox Plugin](https://code.google.com/p/google-maps-utility-library-v3/source/browse/trunk/infobox/src/infobox.js?r=49) as [Bower dependency](https://github.com/DominikAngerer/google-maps-infobox) and as Window Function so we can easily use it as `shim`. The basic usage by now can look like:

```
<script type="text/template" data-google-map-infobox-template>
    <div class="infobox">
        Hello \{{world}}
    </div>
</script>
```

## MarkerClusterer Support

Google Maps has the possiblilty to use the [MarkerClusterer Plugin](https://github.com/googlemaps/js-marker-clusterer) to directly use it with this setup I've added it as a [Bower dependency](https://github.com/DominikAngerer/google-maps-markercluster-windowed) and as Window Function so we can easily use it as `shim`.

The main use is this simple line of code:

```
this.markerClusterer = new MarkerClusterer(this.map, this.markers, {imagePath: 'https://googlemaps.github.io/js-marker-clusterer/images/m'});
```


## What should I do if I don't need the `Infobox Support` or the `MarkerClusterer Support`?

Our `gulp` will directly generate the `vender.js` according to the `bower.json`. So If you don't need the `Infobox Support` just remove that line of the `bower.json` - same for the `MarkerClusterer Support`. The code in the `MapController` only initialize those features if the dependency was found.


#### No `Infobox Support`

```
{
  "name": "typescript-google-maps",
  "version": "0.0.0",
  "dependencies": {
    "google-maps-markercluster-windowed": "*"
  },
  "devDependencies": {},
  "overrides": {}
}
```

#### No `MarkerClusterer Support`

```
{
  "name": "typescript-google-maps",
  "version": "0.0.0",
  "dependencies": {
    "google-maps-infobox-windowed": "*"
  },
  "devDependencies": {},
  "overrides": {}
}

```

#### No `Infobox Support` && `MarkerClusterer Support`

```
{
  "name": "typescript-google-maps",
  "version": "0.0.0",
  "dependencies": {
  },
  "devDependencies": {},
  "overrides": {}
}

```

## Licence
Typescript Google Maps
Copyright © 2017 Dominik Angerer

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
