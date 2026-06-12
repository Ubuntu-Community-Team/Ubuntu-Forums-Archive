---
title: "Error al ejecutar Ka lite, posible error en la instalación."
date: 2018-09-26
forum: Centroamerica Team
---

### Post by cmn-15 on 2018-09-26
Hola!
¡Buenas noches!

Estoy tratando de instalar Ka lite de Khan Academy en Ubuntu 18.04 64 bits Gnome:
[https://ka-lite.readthedocs.io/en/latest/installguide/install_all.html#linux]("http://https://ka-lite.readthedocs.io/en/latest/installguide/install_all.html#linux")

Aparentemente si se instala, pero al momento de iniciarlo me da la siguiente dirección:
[http://127.0.0.1:7005/](http://127.0.0.1:7005/) a donde ingreso, pero todo queda en blanco.

¿Alguien tiene alguna idea de como solucionarlo?

Estoy instalando en Ubuntu 18.04 de 64 bits.


/home/user/.kalite/server.log contiene:

[PHP][INFO] [2018-09-22 21:16:51,475] cherrypy.error: [22/Sep/2018:21:16:51] ENGINE Listening for SIGHUP.
[INFO] [2018-09-22 21:16:51,476] cherrypy.error: [22/Sep/2018:21:16:51] ENGINE Listening for SIGTERM.
[INFO] [2018-09-22 21:16:51,476] cherrypy.error: [22/Sep/2018:21:16:51] ENGINE Listening for SIGUSR1.
[INFO] [2018-09-22 21:16:51,477] cherrypy.error: [22/Sep/2018:21:16:51] ENGINE Bus STARTING
[INFO] [2018-09-22 21:16:51,477] cherrypy.error: [22/Sep/2018:21:16:51]  Loading and serving the Django application
[INFO] [2018-09-22 21:16:51,490] cherrypy.error: [22/Sep/2018:21:16:51] ENGINE Started monitor thread '_TimeoutMonitor'.
[INFO] [2018-09-22 21:16:51,716] cherrypy.error: [22/Sep/2018:21:16:51] ENGINE Serving on http://0.0.0.0:7005
[INFO] [2018-09-22 21:16:51,716] cherrypy.error: [22/Sep/2018:21:16:51] ENGINE Bus STARTED
[ERROR] [2018-09-22 21:16:57,402] cherrypy.error: [22/Sep/2018:21:16:57]  ENGINE GEOSException(u'Could not parse version info string  "3.6.2-CAPI-1.10.2 4d2925d6"',)
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/kalite/packages/dist/cherrypy/wsgiserver/wsgiserver2.py", line 1353, in communicate
    req.respond()
  File "/usr/lib/python2.7/dist-packages/kalite/packages/dist/cherrypy/wsgiserver/wsgiserver2.py", line 868, in respond
    self.server.gateway(self).respond()
  File "/usr/lib/python2.7/dist-packages/kalite/packages/dist/cherrypy/wsgiserver/wsgiserver2.py", line 2257, in respond
    response = self.req.server.wsgi_app(self.env, self.start_response)
  File "/usr/lib/python2.7/dist-packages/kalite/packages/dist/cherrypy/_cptree.py", line 299, in __call__
    return app(environ, start_response)
  File "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/handlers/wsgi.py", line 255, in __call__
    response = self.get_response(request)
  File "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/handlers/base.py", line 178, in get_response
    response = self.handle_uncaught_exception(request, resolver, sys.exc_info())
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/handlers/base.py",  line 220, in handle_uncaught_exception
    if resolver.urlconf_module is None:
  File "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/urlresolvers.py", line 342, in urlconf_module
    self._urlconf_module = import_module(self.urlconf_name)
  File "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/utils/importlib.py", line 35, in import_module
    __import__(name)
  File "/usr/lib/python2.7/dist-packages/kalite/distributed/urls.py", line 14, in <module>
    from . import api_urls
  File "/usr/lib/python2.7/dist-packages/kalite/distributed/api_urls.py", line 12, in <module>
    import kalite.coachreports.api_urls
  File "/usr/lib/python2.7/dist-packages/kalite/coachreports/api_urls.py", line 3, in <module>
    from .api_resources import PlaylistProgressResource, PlaylistProgressDetailResource
  File "/usr/lib/python2.7/dist-packages/kalite/coachreports/api_resources.py", line 3, in <module>
    from tastypie.resources import Resource
  File "/usr/lib/python2.7/dist-packages/kalite/packages/dist/tastypie/resources.py", line 20, in <module>
    from django.contrib.gis.db.models.fields import GeometryField
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/__init__.py",  line 5, in <module>
    from django.contrib.gis.db.models.aggregates import *
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/aggregates.py",  line 2, in <module>
    from django.contrib.gis.db.models.sql import GeomField
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/sql/__init__.py",  line 2, in <module>
    from django.contrib.gis.db.models.sql.query import GeoQuery
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/sql/query.py",  line 4, in <module>
    from django.contrib.gis.db.models.fields import GeometryField
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/fields.py",  line 4, in <module>
    from django.contrib.gis import forms
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/forms/__init__.py",  line 2, in <module>
    from django.contrib.gis.forms.fields import GeometryField
  File "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/forms/fields.py", line 8, in <module>
    from django.contrib.gis.geos import GEOSException, GEOSGeometry
  File "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/__init__.py", line 6, in <module>
    from django.contrib.gis.geos.geometry import GEOSGeometry, wkt_regex, hex_regex
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/geometry.py",  line 16, in <module>
    from django.contrib.gis.geos.coordseq import GEOSCoordSeq
  File "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/coordseq.py", line 9, in <module>
    from django.contrib.gis.geos.libgeos import CS_PTR
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/libgeos.py",  line 131, in <module>
    _verinfo = geos_version_info()
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/libgeos.py",  line 126, in geos_version_info
    raise GEOSException('Could not parse version info string "%s"' % ver)
GEOSException: Could not parse version info string "3.6.2-CAPI-1.10.2 4d2925d6"

[ERROR] [2018-09-22 21:16:59,482] cherrypy.error: [22/Sep/2018:21:16:59]  ENGINE GEOSException(u'Could not parse version info string  "3.6.2-CAPI-1.10.2 4d2925d6"',)
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/kalite/packages/dist/cherrypy/wsgiserver/wsgiserver2.py", line 1353, in communicate
    req.respond()
  File "/usr/lib/python2.7/dist-packages/kalite/packages/dist/cherrypy/wsgiserver/wsgiserver2.py", line 868, in respond
    self.server.gateway(self).respond()
  File "/usr/lib/python2.7/dist-packages/kalite/packages/dist/cherrypy/wsgiserver/wsgiserver2.py", line 2257, in respond
    response = self.req.server.wsgi_app(self.env, self.start_response)
  File "/usr/lib/python2.7/dist-packages/kalite/packages/dist/cherrypy/_cptree.py", line 299, in __call__
    return app(environ, start_response)
  File "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/handlers/wsgi.py", line 255, in __call__
    response = self.get_response(request)
  File "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/handlers/base.py", line 178, in get_response
    response = self.handle_uncaught_exception(request, resolver, sys.exc_info())
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/handlers/base.py",  line 220, in handle_uncaught_exception
    if resolver.urlconf_module is None:
  File "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/urlresolvers.py", line 342, in urlconf_module
    self._urlconf_module = import_module(self.urlconf_name)
  File "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/utils/importlib.py", line 35, in import_module
    __import__(name)
  File "/usr/lib/python2.7/dist-packages/kalite/distributed/urls.py", line 14, in <module>
    from . import api_urls
  File "/usr/lib/python2.7/dist-packages/kalite/distributed/api_urls.py", line 12, in <module>
    import kalite.coachreports.api_urls
  File "/usr/lib/python2.7/dist-packages/kalite/coachreports/api_urls.py", line 3, in <module>
    from .api_resources import PlaylistProgressResource, PlaylistProgressDetailResource
  File "/usr/lib/python2.7/dist-packages/kalite/coachreports/api_resources.py", line 3, in <module>
    from tastypie.resources import Resource
  File "/usr/lib/python2.7/dist-packages/kalite/packages/dist/tastypie/resources.py", line 20, in <module>
    from django.contrib.gis.db.models.fields import GeometryField
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/__init__.py",  line 5, in <module>
    from django.contrib.gis.db.models.aggregates import *
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/aggregates.py",  line 2, in <module>
    from django.contrib.gis.db.models.sql import GeomField
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/sql/__init__.py",  line 2, in <module>
    from django.contrib.gis.db.models.sql.query import GeoQuery
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/sql/query.py",  line 4, in <module>
    from django.contrib.gis.db.models.fields import GeometryField
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/fields.py",  line 4, in <module>
    from django.contrib.gis import forms
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/forms/__init__.py",  line 2, in <module>
    from django.contrib.gis.forms.fields import GeometryField
  File "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/forms/fields.py", line 8, in <module>
    from django.contrib.gis.geos import GEOSException, GEOSGeometry
  File "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/__init__.py", line 6, in <module>
    from django.contrib.gis.geos.geometry import GEOSGeometry, wkt_regex, hex_regex
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/geometry.py",  line 16, in <module>
    from django.contrib.gis.geos.coordseq import GEOSCoordSeq
  File "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/coordseq.py", line 9, in <module>
    from django.contrib.gis.geos.libgeos import CS_PTR
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/libgeos.py",  line 131, in <module>
    _verinfo = geos_version_info()
  File  "/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/libgeos.py",  line 126, in geos_version_info
    raise GEOSException('Could not parse version info string "%s"' % ver)
GEOSException: Could not parse version info string "3.6.2-CAPI-1.10.2 4d2925d6"

[/PHP]
Cuando ejecuto

** kalite manage setup**

Traceback (most recent call last):
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/management/base.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]224[/COLOR][COLOR=#339933],[/COLOR] in run_from_argv
    [COLOR=#000000]**self**[/COLOR][COLOR=#339933].[/COLOR]execute[COLOR=#009900]([/COLOR][COLOR=#339933]*[/COLOR]args[COLOR=#339933],[/COLOR] [COLOR=#339933]**[/COLOR]options[COLOR=#339933].[/COLOR]__dict__[COLOR=#009900])[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/management/base.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]263[/COLOR][COLOR=#339933],[/COLOR] in execute
    output [COLOR=#339933]=[/COLOR] [COLOR=#000000]**self**[/COLOR][COLOR=#339933].[/COLOR]handle[COLOR=#009900]([/COLOR][COLOR=#339933]*[/COLOR]args[COLOR=#339933],[/COLOR] [COLOR=#339933]**[/COLOR]options[COLOR=#009900])[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/distributed/management/commands/setup.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]477[/COLOR][COLOR=#339933],[/COLOR] in handle
    call_command[COLOR=#009900]([/COLOR][COLOR=#0000ff]"collectstatic_js_reverse"[/COLOR][COLOR=#339933],[/COLOR] interactive[COLOR=#339933]=[/COLOR][COLOR=#009900]**False**[/COLOR][COLOR=#009900])[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/management/__init__.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]161[/COLOR][COLOR=#339933],[/COLOR] in call_command
    [COLOR=#b1b100]return[/COLOR] klass[COLOR=#339933].[/COLOR]execute[COLOR=#009900]([/COLOR][COLOR=#339933]*[/COLOR]args[COLOR=#339933],[/COLOR] [COLOR=#339933]**[/COLOR]defaults[COLOR=#009900])[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/management/base.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]263[/COLOR][COLOR=#339933],[/COLOR] in execute
    output [COLOR=#339933]=[/COLOR] [COLOR=#000000]**self**[/COLOR][COLOR=#339933].[/COLOR]handle[COLOR=#009900]([/COLOR][COLOR=#339933]*[/COLOR]args[COLOR=#339933],[/COLOR] [COLOR=#339933]**[/COLOR]options[COLOR=#009900])[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/dist/django_js_reverse/management/commands/collectstatic_js_reverse.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]26[/COLOR][COLOR=#339933],[/COLOR] in handle
    content [COLOR=#339933]=[/COLOR] urls_js[COLOR=#009900]([/COLOR][COLOR=#009900])[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/dist/django_js_reverse/views.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]50[/COLOR][COLOR=#339933],[/COLOR] in urls_js
    [COLOR=#0000ff]'urls'[/COLOR][COLOR=#339933]:[/COLOR] sorted[COLOR=#009900]([/COLOR][[COLOR=#990000]list[/COLOR]]("http://www.php.net/list")[COLOR=#009900]([/COLOR]prepare_url_list[COLOR=#009900]([/COLOR]default_urlresolver[COLOR=#009900])[/COLOR][COLOR=#009900])[/COLOR][COLOR=#009900])[/COLOR][COLOR=#339933],[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/dist/django_js_reverse/views.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]74[/COLOR][COLOR=#339933],[/COLOR] in prepare_url_list
    [COLOR=#b1b100]for[/COLOR] url_name in urlresolver[COLOR=#339933].[/COLOR]reverse_dict[COLOR=#339933].[/COLOR]keys[COLOR=#009900]([/COLOR][COLOR=#009900])[/COLOR][COLOR=#339933]:[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/urlresolvers.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]297[/COLOR][COLOR=#339933],[/COLOR] in reverse_dict
    [COLOR=#000000]**self**[/COLOR][COLOR=#339933].[/COLOR]_populate[COLOR=#009900]([/COLOR][COLOR=#009900])[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/urlresolvers.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]263[/COLOR][COLOR=#339933],[/COLOR] in _populate
    [COLOR=#b1b100]for[/COLOR] pattern in reversed[COLOR=#009900]([/COLOR][COLOR=#000000]**self**[/COLOR][COLOR=#339933].[/COLOR]url_patterns[COLOR=#009900])[/COLOR][COLOR=#339933]:[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/urlresolvers.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]347[/COLOR][COLOR=#339933],[/COLOR] in url_patterns
    patterns [COLOR=#339933]=[/COLOR] getattr[COLOR=#009900]([/COLOR][COLOR=#000000]**self**[/COLOR][COLOR=#339933].[/COLOR]urlconf_module[COLOR=#339933],[/COLOR] [COLOR=#0000ff]"urlpatterns"[/COLOR][COLOR=#339933],[/COLOR] [COLOR=#000000]**self**[/COLOR][COLOR=#339933].[/COLOR]urlconf_module[COLOR=#009900])[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/core/urlresolvers.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]342[/COLOR][COLOR=#339933],[/COLOR] in urlconf_module
    [COLOR=#000000]**self**[/COLOR][COLOR=#339933].[/COLOR]_urlconf_module [COLOR=#339933]=[/COLOR] import_module[COLOR=#009900]([/COLOR][COLOR=#000000]**self**[/COLOR][COLOR=#339933].[/COLOR]urlconf_name[COLOR=#009900])[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/utils/importlib.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]35[/COLOR][COLOR=#339933],[/COLOR] in import_module
    __import__[COLOR=#009900]([/COLOR]name[COLOR=#009900])[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/distributed/urls.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]14[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    from [COLOR=#339933].[/COLOR] import api_urls
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/distributed/api_urls.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]12[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    import kalite[COLOR=#339933].[/COLOR]coachreports[COLOR=#339933].[/COLOR]api_urls
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/coachreports/api_urls.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]3[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    from [COLOR=#339933].[/COLOR]api_resources import PlaylistProgressResource[COLOR=#339933],[/COLOR] PlaylistProgressDetailResource
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/coachreports/api_resources.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]3[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    from tastypie[COLOR=#339933].[/COLOR]resources import Resource
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/dist/tastypie/resources.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]20[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    from django[COLOR=#339933].[/COLOR]contrib[COLOR=#339933].[/COLOR]gis[COLOR=#339933].[/COLOR]db[COLOR=#339933].[/COLOR]models[COLOR=#339933].[/COLOR]fields import GeometryField
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/__init__.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]5[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    from django[COLOR=#339933].[/COLOR]contrib[COLOR=#339933].[/COLOR]gis[COLOR=#339933].[/COLOR]db[COLOR=#339933].[/COLOR]models[COLOR=#339933].[/COLOR]aggregates import [COLOR=#339933]*[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/aggregates.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]2[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    from django[COLOR=#339933].[/COLOR]contrib[COLOR=#339933].[/COLOR]gis[COLOR=#339933].[/COLOR]db[COLOR=#339933].[/COLOR]models[COLOR=#339933].[/COLOR]sql import GeomField
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/sql/__init__.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]2[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    from django[COLOR=#339933].[/COLOR]contrib[COLOR=#339933].[/COLOR]gis[COLOR=#339933].[/COLOR]db[COLOR=#339933].[/COLOR]models[COLOR=#339933].[/COLOR]sql[COLOR=#339933].[/COLOR]query import GeoQuery
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/sql/query.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]4[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    from django[COLOR=#339933].[/COLOR]contrib[COLOR=#339933].[/COLOR]gis[COLOR=#339933].[/COLOR]db[COLOR=#339933].[/COLOR]models[COLOR=#339933].[/COLOR]fields import GeometryField
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/db/models/fields.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]4[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    from django[COLOR=#339933].[/COLOR]contrib[COLOR=#339933].[/COLOR]gis import forms
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/forms/__init__.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]2[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    from django[COLOR=#339933].[/COLOR]contrib[COLOR=#339933].[/COLOR]gis[COLOR=#339933].[/COLOR]forms[COLOR=#339933].[/COLOR]fields import GeometryField
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/forms/fields.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]8[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    from django[COLOR=#339933].[/COLOR]contrib[COLOR=#339933].[/COLOR]gis[COLOR=#339933].[/COLOR]geos import GEOSException[COLOR=#339933],[/COLOR] GEOSGeometry
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/__init__.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]6[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    from django[COLOR=#339933].[/COLOR]contrib[COLOR=#339933].[/COLOR]gis[COLOR=#339933].[/COLOR]geos[COLOR=#339933].[/COLOR]geometry import GEOSGeometry[COLOR=#339933],[/COLOR] wkt_regex[COLOR=#339933],[/COLOR] hex_regex
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/geometry.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]16[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    from django[COLOR=#339933].[/COLOR]contrib[COLOR=#339933].[/COLOR]gis[COLOR=#339933].[/COLOR]geos[COLOR=#339933].[/COLOR]coordseq import GEOSCoordSeq
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/coordseq.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]9[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    from django[COLOR=#339933].[/COLOR]contrib[COLOR=#339933].[/COLOR]gis[COLOR=#339933].[/COLOR]geos[COLOR=#339933].[/COLOR]libgeos import CS_PTR
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/libgeos.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]131[/COLOR][COLOR=#339933],[/COLOR] in [COLOR=#339933]<[/COLOR]module[COLOR=#339933]>[/COLOR]
    _verinfo [COLOR=#339933]=[/COLOR] geos_version_info[COLOR=#009900]([/COLOR][COLOR=#009900])[/COLOR]
  [[COLOR=#990000]File[/COLOR]]("http://www.php.net/file") [COLOR=#0000ff]"/usr/lib/python2.7/dist-packages/kalite/packages/bundled/django/contrib/gis/geos/libgeos.py"[/COLOR][COLOR=#339933],[/COLOR] line [COLOR=#cc66cc]126[/COLOR][COLOR=#339933],[/COLOR] in geos_version_info
    raise GEOSException[COLOR=#009900]([/COLOR][COLOR=#0000ff]'Could not parse version info string "%s"'[/COLOR] [COLOR=#339933]%[/COLOR] ver[COLOR=#009900])[/COLOR]
GEOSException[COLOR=#339933]:[/COLOR] Could not parse version info string [COLOR=#0000ff]"3.7.0-CAPI-1.11.0 673b9939"[/COLOR]



Espero me puedan orientar!

¡gracias!

---

### Post by WHK on 2019-01-18
Hola, eso me huele a un bug del mismo desarrollo, especialmente en la función "geos_version_info()" de python, el cual no es capaz de procesar el texto de la versión de CAPI, probablemente está intentando utilizar un componente con una versión inesperada por el desarrollador.

En cualquier caso no es un problema de ubuntu sino del desarrollador de la aplicación. Te sugiero que te contactes con ellos y reportes el fallo para obtener soporte.

Saludos.

---

