# tile-cache-php
PHP caching proxy between tile server and your map application. To save bandwith of the real tile servers.

## usage
Change variables in index.php.

### apache
Set RewriteBase in .htaccess.

### nginx
Use in your nginx site definition. Do _not_ use any redirects or other fancy configuration.
```
location / {
        try_files $uri /index.php;
    }
```

### go
Use `https://yourdomain.com/appfolder/{zoom}/{x}/{y}.png` as tile url and it serves a cached tile from e.g. `http://c.tile.openstreetmap.org/{zoom}/{x}/{y}.png`

Add other tile server by extending the $maptypes array.

### leaflet Example
```
var tile_osm = L.tileLayer('https://yourdomain.com/maps/tile-cache/osm/{z}/{x}/{y}.png', {
  attribution: '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors'
}).addTo(map);
```
