# `tupu` - Fast geodesic distances in Python

Tupu is a Python project centered around efficiently computing geodesic distances between points or lists. Features include:

- Distances to a given point (e.g. distances from each point in a list to NYC)
- Nearest neighbors: distances to the closest point in another list (e.g. distances from each point to a city), and the identity of such point
- Number of neighbors: number of points of another list within a certain distance or buffer.

Its main goals are to be fast and simple to use.
However, the project is mostly personal, so although issues and pull requests are welcome,
I won't work on feature requests.


## Dev Install

After cloning the repo and opening the panflute folder:

`python setup.py install`
: installs the package locally

`python setup.py develop`
: installs locally with a symlink so changes are automatically updated


## Usage

From Python:

```python
import tupu
# TODO...
```

From the command line:

```bash
tupu some_cities.csv?id=uid --output=augmented.tsv --distance=dist_ny,40.7143,-74.0060
```

(See also [examples/README.md])


## Dependencies:

- [`rtree`](http://toblerity.org/rtree/) (wrapper around [`libspatialindex`](https://libspatialindex.org/)). Windows binaries [here](https://www.lfd.uci.edu/~gohlke/pythonlibs/#rtree)
- [`pyproj`](https://github.com/pyproj4/pyproj) (wrapper around [`proj4`](https://proj4.org/))


## Why "tupu"?

Tupu was one of the Inca measures of distance, equivalent to about 130 cm.
I would have preferred to use "topo", but it's already a quite popular name on Github, and has other meanings.

![Text](docs/incidence_of_travel_moore_p208.png)

[Jerry D. Moore, "Incidence of Travel: Recent Journeys in Ancient South America", p.208](https://books.google.com/books?id=B_kmDgAAQBAJ&pg=PA208&lpg=PA208)





## Why not geopandas, etc.?

Earlier tests deemed them too slow/complicated, but there might be workarounds. EG:

https://stackoverflow.com/questions/54804073/how-can-i-accelerate-a-geopandas-spatial-join/54804074#54804074


## Limitations

- Not parallelized, although that should be trivial
- Not Cython, although most of the heavy load is already in C.
- Only deals with points, not with lines/polygons
- Currently only stores distance to closest city (although allowing more is trivial)
- Currently does not compute number of points within a given distance (although allowing more is trivial)
