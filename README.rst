================================
Googe App Engine Installer 1.9.4
================================

This package installs the
`Google App Engine SDK 1.9.4 <https://developers.google.com/appengine/downloads#Google_App_Engine_SDK_for_Python>`_
to the ``site-packages`` directory of the current Python interpreter
so that you can use ``from google import appengine`` outside the
``dev_appserver.py`` runtime. This is useful if you want to use the
`google.appengine.ext.testbed <https://developers.google.com/appengine/docs/python/tools/localunittesting>`_
package in your tests.

It also makes all of the GAE commands like ``dev_appserver.py``,
``bulkloader.py``, etc. globaly available without the ``.py`` extension.

The installer works wit `Virtualenv <https://virtualenv.pypa.io/>`_.

The **version** of this package mirrors the
`GAE SDK <https://developers.google.com/appengine/downloads#Google_App_Engine_SDK_for_Python>`_
version (currently 1.9.4) and if there will be a new release of the SDK,
there will be a corresponding release of this package too.

Usage
-----

Create a virtual environment

.. code-block:: bash

    $ virtualenv e
    $ . e/bin/activate

Install with pip,

.. code-block:: bash

    $(e) pip install gae_installer

or with easy_install,

.. code-block:: bash

    $(e) easy_install gae_installer

or manually

.. code-block:: bash

    $(e) git colone https://github.com/peterhudec/gae_installer.git
    $(e) python gae_installer/setup.py install
    $(e) rm -rf gae_installer

The installation will take a while. After it is complete, you should be able to
import the ``google`` package:

.. code-block:: bash

    (e)$ python -c "from google import appengine; print appengine.__file__"
    /Users/peterhudec/demo/e/lib/python2.7/site-packages/google_appengine/google/appengine/__init__.pyc


And the GAE executables should be in the ``./e/bin/`` directory.

.. code-block:: bash

    $(e) ls -l ./e/bin/
    total 232
    -rw-r--r--  1 peterhudec  staff   2224 May 14 12:38 activate
    -rw-r--r--  1 peterhudec  staff   1280 May 14 12:38 activate.csh
    -rw-r--r--  1 peterhudec  staff   2493 May 14 12:38 activate.fish
    -rw-r--r--  1 peterhudec  staff   1129 May 14 12:38 activate_this.py
    -rwxr-xr-x  1 peterhudec  staff     42 May 13 19:36 api_server
    -rwxr-xr-x  1 peterhudec  staff     42 May 13 19:48 backends_conversion
    -rwxr-xr-x  1 peterhudec  staff     42 May 13 19:48 bulkload_client
    -rwxr-xr-x  1 peterhudec  staff     42 May 13 19:48 bulkloader
    -rwxr-xr-x  1 peterhudec  staff     42 May 13 19:36 dev_appserver
    -rwxr-xr-x  1 peterhudec  staff     42 May 13 19:48 download_appstats
    -rwxr-xr-x  1 peterhudec  staff    271 May 14 12:38 easy_install
    -rwxr-xr-x  1 peterhudec  staff    271 May 14 12:38 easy_install-2.7
    -rwxr-xr-x  1 peterhudec  staff     42 May 13 19:48 endpointscfg
    -rwxr-xr-x  1 peterhudec  staff     42 May 13 19:48 gen_protorpc
    -rwxr-xr-x  1 peterhudec  staff     69 May 13 19:35 get_gae_dir
    -rwxr-xr-x  1 peterhudec  staff     42 May 13 19:48 google_sql
    -rwxr-xr-x  1 peterhudec  staff     42 May 13 19:49 old_dev_appserver
    -rwxr-xr-x  1 peterhudec  staff     42 May 13 19:49 php_cli
    -rwxr-xr-x  1 peterhudec  staff    243 May 14 12:38 pip
    -rwxr-xr-x  1 peterhudec  staff    243 May 14 12:38 pip2
    -rwxr-xr-x  1 peterhudec  staff    243 May 14 12:38 pip2.7
    -rwxr-xr-x  1 peterhudec  staff  12752 May 14 12:38 python
    lrwxr-xr-x  1 peterhudec  staff      6 May 14 12:38 python2 -> python
    lrwxr-xr-x  1 peterhudec  staff      6 May 14 12:38 python2.7 -> python
    -rwxr-xr-x  1 peterhudec  staff     42 May 13 19:49 remote_api_shell
    -rwxr-xr-x  1 peterhudec  staff     42 May 13 19:49 wrapper_util

How It Works
------------

Running ``python setup.py install`` downloads and extracts the
`Google App Engine SDK <https://developers.google.com/appengine/downloads#Google_App_Engine_SDK_for_Python>`_
for *Linux/Other Platforms* version **1.9.4** from
https://storage.googleapis.com/appengine-sdks/featured/google_appengine_1.9.4.zip
and extracts it into ``site-packages/google_appengine`` of the current Python
interpreter and creates the ``site-packages/google_appengine.pth`` file with
relative path to the ``google_appengine`` directory. It also creates Bash
executables in the *scripts directory* of the current Python interpreter
which wrap the GAE Python executables in the ``site-packages/google_appengine``
directory.