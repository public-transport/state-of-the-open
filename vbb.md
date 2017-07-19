# the state of open public transport in [Berlin & Brandenburg](https://en.wikipedia.org/wiki/Berlin/Brandenburg_Metropolitan_Region)

## recap

There are two major public transport providers in Berlin:

- [Berlin public transport agency (BVG)](https://en.wikipedia.org/wiki/Berliner_Verkehrsbetriebe), running subway (*U-Bahn*), tram, bus and ferry. It is owned by the city of Berlin.
- [S-Bahn Berlin](https://en.wikipedia.org/wiki/Berlin_S-Bahn), running the *S-Bahn* light rail commuter train, owned by [Deutsche Bahn](https://en.wikipedia.org/wiki/DB_Regio).

Together with many smaller providers, they form the [Berlin & Brandenburg public transport association called VBB](https://en.wikipedia.org/wiki/Verkehrsverbund_Berlin-Brandenburg).

## existing data & services

### static data

**VBB [publishes](https://daten.berlin.de/kategorie/verkehr) open [GTFS](https://developers.google.com/transit/gtfs/) data** with the following information:

- a list of stations, including their location and stops
- a list of lines, with mode of transport and all variants of how they run
- all schedules stopovers of all lines for the coming months

### realtime API

It also provides **[an API](http://www.vbb.de/de/article/fahrplan/webservices/schnittstellen-fuer-webentwickler/5070.html#rest-schnittstelle) you can request a key for**. This API provides you with

- realtime departures at any station
- realtime routing from A to B
- search among all stations

Along with many other parts of their digital infrastructure, this API is being provided in a package called [*HAFAS*](https://de.wikipedia.org/wiki/HAFAS), developed by the German contractor [*HaCon*](http://hacon.de).

Both the static data and the API include all public transport providers operating in Berlin & Brandenburg.

### elevator availability API

There is an [RSS feed indicating the status of elevators at the stations](http://www.vbb.de/de/article/fahrplan/webservices/aufzugsstoerungen-als-rss-feed/44096.html).

## missing data

- **locations of the station entrances** – [vbb-osm-relations](https://github.com/derhuerst/vbb-osm-relations#vbb-osm-relations) tries to fill in using [OSM](https://openstreetmap.org/).
- **operators of each station** – [vbb-station-operators](https://github.com/derhuerst/vbb-station-operators#vbb-station-operators) has manually collected data.
- **data about fare zones** – [vbb-fare-zones](https://github.com/derhuerst/vbb-fare-zones#vbb-fare-zones) provides a heuristic.
- **line colors** (which are essential in Berlin) – [vbb-util is an inofficial collection](https://github.com/derhuerst/vbb-util/blob/master/lines/colors.json).

## subpar data

- Some **stations are split apart**. – [merge-vbb-stations](https://github.com/derhuerst/merge-vbb-stations#merge-vbb-stations) provides a heuristic to merge them.
- The **[static GTFS](https://vbb-gtfs.jannisr.de/latest/) has no proper schedules**. It has every single trip of every single line as an exception.
- The data on **station entrances is outdated and incomplete**. [vbb-entrances](https://github.com/derhuerst/vbb-entrances#vbb-entrances) has the latest version.
- Both the [static GTFS](https://vbb-gtfs.jannisr.de/latest/) and the API have **no canonical format for station names**. One should be able to get the station name (without "S+U") without [guesswork](https://github.com/derhuerst/vbb-short-station-name).
