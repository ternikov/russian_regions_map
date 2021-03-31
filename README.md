# Russian Regions Map. Antimeridian Fixed

**Issue**: `180° meridian` (`International Date Line` or `Anti-Meridian`) splits [Chukotka region](https://wiki.openstreetmap.org/wiki/180th_meridian) on the map:
* [Related Issue #1](https://gis.stackexchange.com/questions/123038/mapping-russia-intl-dateline-splitting-polygon)
* [Related Issue #2](https://gis.stackexchange.com/questions/192306/unwanted-display-of-180-meridian-in-map?noredirect=1&lq=1)
* [Related Issue #3](https://gis.stackexchange.com/questions/315859/removing-180th-meridian-line-on-map-of-russia)

![antimeridian issue](https://github.com/ternikov/russian_regions_map/blob/main/maps.png?raw=true)

**Workflow**:
1. Basemap: `current_russia_mercator` from https://github.com/logvik/d3_russian_map
2. QGIS processed (split and merge Chukotka polygons)
3. R processed using `mapzoom.R` (recalculation of negative longitudes) from https://github.com/Sobach/R.rus.map.zoom
4. GeoJSON rendering

---
**Filename**: [**`russian_regions_fix.geojson`**](https://github.com/ternikov/russian_regions_map/blob/main/russian_regions_fix.geojson)

>Simple feature collection with 85 features and 20 fields

| Property | Value |
|-----------|------------|
|layer |`russia`|
|geometry type | `MULTIPOLYGON`|
|dimension     | `XY`|
|bbox          | `xmin: 19.64447 ymin: 41.18985 xmax: 190.3384 ymax: 81.85732`|
|epsg (SRID)   | `4326`|
|proj4string   | `+proj=longlat +datum=WGS84 +no_defs`|

---
**Usage**:
* Map with [EPSG:4326 (WGS 84) projection](https://spatialreference.org/ref/epsg/wgs-84/)
* Map with [SR-ORG:8568 (Albers Equal Area Russia) projection](https://spatialreference.org/ref/sr-org/albers-equal-area-russia/)
* [Leaflet Usage (for R)](https://rstudio.github.io/leaflet/projections.html):
```
crs <- leaflet::leafletCRS(crsClass = "L.Proj.CRS", code = "ESRI:102003",
                proj4def = "+proj=aea +lat_0=56 +lon_0=100 +lat_1=50 +lat_2=70 +x_0=0 +y_0=0 +datum=WGS84 +units=m +no_defs",
                resolutions = 1.5^(25:15))
```

<a href="https://www.buymeacoffee.com/ternikov" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/orange_img.png" alt="Buy Me A Coffee" style="height: 41px !important;width: 174px !important;box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;-webkit-box-shadow: 0px 3px 2px 0px rgba(190, 190, 190, 0.5) !important;" ></a>
