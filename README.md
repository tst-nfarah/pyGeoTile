[![Build Status](https://travis-ci.org/tst-nfarah/pyGeoTile.svg?branch=master)](https://travis-ci.org/tst-nfarah/pyGeoTile)
[![Coverage Status](https://coveralls.io/repos/github/tst-nfarah/pyGeoTile/badge.svg?branch=codecoverage)](https://coveralls.io/github/tst-nfarah/pyGeoTile?branch=codecoverage)
# pyGeoTile
Python package to handle tiles and points of different projections, in particular WGS 84 (Latitude, Longitude), Spherical Mercator (Meters), Pixel Pyramid and Tiles (TMS, Google, QuadTree)

## Usage
The package pyGeoTile consist of two main classes, namely Point and Tile.
As already mentioned they allow you to convert various geo projections.

The full API documentation could be found under http://pygeotile.readthedocs.io

### Point
Example of the class Point.
```python
from pygeotile.point import Point

meter_x, meter_y, zoom = -9757148.442088600, 5138517.444985110, 19  # meters in Spherical Mercator EPSG:900913

point = Point.from_meters(meter_x=meter_x, meter_y=meter_y)

print('Pixels: ', point.pixels(zoom=zoom))  # Pixels:  (34430592, 49899136)
print('Lat/Lon: ', point.latitude_longitude)  # Lat/Lon:  (41.84987190947754, -87.64995574951166)
```

### Tile
Example of the class Tile.
```python
from pygeotile.tile import Tile

tms_x, tms_y, zoom = 134494, 329369, 19
tile = Tile.from_tms(tms_x=tms_x, tms_y=tms_y, zoom=19)  # Tile Map Service (TMS) X Y and zoom

print('QuadTree: ', tile.quad_tree)  # QuadTree:  0302222310303211330
print('Google: ', tile.google)  # Google:  (134494, 194918)
```

## Installation
To install pyGeoTile, simply:
```bash
pip install pyGeoTile

```
pyGeoTile officially supports Python 2.7, 3.4, 3.5, 3.6, 3.7, 3.5-dev, 3.6-dev, 3.7-dev, nightly and PyPy3.

## Notes
This repository is inspired by:
 - Tiles à la Google Maps: http://www.maptiler.org/google-maps-coordinates-tile-bounds-projection/
 - Bing Maps Tile System: https://msdn.microsoft.com/en-us/library/bb259689.aspx
 - Showing pixel and tile coordinates: https://developers.google.com/maps/documentation/javascript/examples/map-coordinates?hl=de
 - Mercantile: https://github.com/mapbox/mercantile
 
## Example usage
An example usage of the pyGeoTile library is the tool [GeoDex](https://github.com/developmentseed/geodex).
It is able to find all geospatial tile indices contained in an arbitrary boundary at an arbitrary zoom.

We are happy to hear about other projects which are using pyGeoTile and we would like to mention them. So don't hesitate to contact us.