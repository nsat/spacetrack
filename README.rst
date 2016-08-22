spacetrack
-------------

|PyPI Version| |Documentation| |Travis| |Coverage| |Python Version| |MIT License|

spacetrack is a python module for `Space-Track <https://www.space-track.org>`__

Installation
~~~~~~~~~~~~

First, make an account on https://www.space-track.org/.
You'll need to authenticate to use the API.

.. code:: bash

    $ python setup.py install
    $ export SPACETRACK_USER=<email used to make account>
    $ export SPACETRACK_PASS=<password from above>

Example
~~~~~~~

.. code:: python

   >>> import os
   >>> import datetime as dt
   >>> from spacetrack import SpaceTrackClient
   >>> st = SpaceTrackClient(os.environ['SPACETRACK_USER'], os.environ['SPACETRACK_PASS'])

   >>> print(st.tle_latest(norad_cat_id=[25544, 41335], ordinal=1, format='tle'))
   1 25544U 98067A   16179.00000000  .00000000  00000-0  00000-0 0  0000
   2 25544  00.0000   0.0000 0000000  00.0000 000.0000 00.00000000  0000
   1 41335U 16011A   16179.00000000  .00000000  00000-0  00000-0 0  0000
   2 41335  00.0000   0.0000 0000000  00.0000 000.0000 00.00000000  0000

   >>> # Retrieve TLEs after a certain date
   >> print(st.tle(norad_cat_id=[25544], format='json', epoch='>2016-08-16'))

   >>> # Retrieve TLEs between certain dates
   >> print(st.tle(norad_cat_id=[25544], format='json', epoch='2016-08-16--2016-08-19'))

   >>> # Automatic rate limiting
   >>> for satno in my_satnos:
   ...     # Gets limited to <20 requests per minute automatically by blocking
   ...     st.tle(...)

Authors
~~~~~~~
- Frazer McLean <frazer@frazermclean.co.uk>

Documentation
~~~~~~~~~~~~~

For in-depth information, `visit the
documentation <http://spacetrack.readthedocs.org/en/latest/>`__!

Development
~~~~~~~~~~~

spacetrack uses `semantic versioning <http://semver.org>`__

.. |Travis| image:: http://img.shields.io/travis/python-astrodynamics/spacetrack/master.svg?style=flat-square&label=travis
   :target: https://travis-ci.org/python-astrodynamics/spacetrack
.. |PyPI Version| image:: http://img.shields.io/pypi/v/spacetrack.svg?style=flat-square
   :target: https://pypi.python.org/pypi/spacetrack/
.. |Python Version| image:: https://img.shields.io/badge/python-2.7%2C%203-brightgreen.svg?style=flat-square
   :target: https://www.python.org/downloads/
.. |MIT License| image:: http://img.shields.io/badge/license-MIT-blue.svg?style=flat-square
   :target: https://raw.githubusercontent.com/python-astrodynamics/spacetrack/master/LICENSE
.. |Coverage| image:: https://img.shields.io/codecov/c/github/python-astrodynamics/spacetrack/master.svg?style=flat-square
   :target: https://codecov.io/github/python-astrodynamics/spacetrack?branch=master
.. |Documentation| image:: https://img.shields.io/badge/docs-latest-brightgreen.svg?style=flat-square
	:target: http://spacetrack.readthedocs.org/en/latest/
