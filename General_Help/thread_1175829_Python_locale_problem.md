---
title: "Python locale problem?"
date: 2009-06-01
forum: General Help
---

### Post by Ekeluo on 2009-06-01
This is quite annoying. Simply put, as soon as python realizes it is in Nigeria, it breaks itself. Even on the Live CD! How?! Anyway this means alacarte,aptoncd and most importantly, elisa are broken for me. Please Any help that can be rendered will be appreciated.

Terminal outputs:
For alacarte:
```
kels@kels-laptop:~$ alacarte
Traceback (most recent call last):
  File "/usr/bin/alacarte", line 36, in <module>
    main()
  File "/usr/bin/alacarte", line 32, in main
    app = MainWindow(datadir, version, sys.argv)
  File "/usr/lib/python2.6/dist-packages/Alacarte/MainWindow.py", line 50, in __init__
    self.editor = MenuEditor()
  File "/usr/lib/python2.6/dist-packages/Alacarte/MenuEditor.py", line 35, in __init__
    self.locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.6/locale.py", line 478, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
ValueError: unknown locale: en_NG
kels@kels-laptop:~$ 
```

For elisa:
```
kels@kels-laptop:~$ elisa
Launcher core version: 0.5.28
Current core version: 0.5.28
/usr/lib/python2.6/dist-packages/elisa/core/utils/classinit.py:34: UserWarning: ClassInitMeta class is deprecated
  warn("ClassInitMeta class is deprecated")
WARN  MainThread      plugin_registry             Jun 01 19:15:08  plugin elisa-plugin-coherence has the following unmet dependencies: coherence>=0.5.7 (elisa/core/plugin_registry.py:343)
get fences failed: -1
param: 6, val: 0
drm_i915_getparam: -22
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/elisa/core/launcher.py", line 373, in run_application
    reactor.run()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 185, in run
    self.__run()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 225, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 757, in runUntilCurrent
    call.func(*call.args, **call.kw)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/search/search_metaresource_provider.py", line 91, in iterate
    klass = entry.load()
  File "/usr/lib/python2.6/dist-packages/pkg_resources.py", line 1913, in load
    entry = __import__(self.module_name, globals(),globals(), ['__name__'])
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/youtube/searcher.py", line 24, in <module>
    from elisa.plugins.poblesec.search_controller import SearcherEntry
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/poblesec/search_controller.py", line 37, in <module>
    from elisa.plugins.poblesec.widgets.search_results import SearchResultsWidget
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/poblesec/widgets/search_results.py", line 41, in <module>
    _ = install_translation('poblesec')
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 93, in install_translation
    current_locale = get_current_locale()
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 84, in get_current_locale
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.6/locale.py", line 478, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      resource_manager            Jun 01 19:15:10  Creating elisa.plugins.search.search_metaresource_provider:SearchMetaresourceProvider failed. A full traceback can be found at /tmp/elisa_pbJBHq.txt (elisa/core/manager.py:97)
/usr/lib/python2.6/dist-packages/elisa/plugins/base/models/image.py:25: DeprecationWarning: the md5 module is deprecated; use hashlib instead
  import math, md5, os
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 225, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 757, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.6/dist-packages/elisa/core/manager.py", line 101, in load_components_iter
    dfr = plugin_registry.create_component(component_name)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/elisa/core/plugin_registry.py", line 1048, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.6/dist-packages/twisted/python/reflect.py", line 456, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.6/dist-packages/twisted/python/reflect.py", line 392, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/amazon/resource_provider.py", line 33, in <module>
    from elisa.plugins.base.models.image import ImageModel
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/base/models/image.py", line 45, in <module>
    _ = install_translation('base')
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 93, in install_translation
    current_locale = get_current_locale()
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 84, in get_current_locale
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.6/locale.py", line 478, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      resource_manager            Jun 01 19:15:10  Creating elisa.plugins.amazon.resource_provider:AmazonResourceProvider failed. A full traceback can be found at /tmp/elisa_ygKPnU.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
Failure: exceptions.Exception: gnome_screensaver_service - Could not connect to the Gnome ScreenSaver: org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.ScreenSaver was not provided by any .service files

WARN  MainThread      service_manager             Jun 01 19:15:10  Creating elisa.plugins.gnome.gnome_screensaver_service:GnomeScreensaverService failed. A full traceback can be found at /tmp/elisa_Z2GyQ1.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
Failure: elisa.plugins.lirc.lirc_input.NoMappingsFound: Given InputMap 'streamzap.map' not found

WARN  MainThread      input_manager               Jun 01 19:15:10  Creating elisa.plugins.lirc.lirc_input:LircInput failed. A full traceback can be found at /tmp/elisa_1hynRc.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 225, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 757, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.6/dist-packages/elisa/core/manager.py", line 101, in load_components_iter
    dfr = plugin_registry.create_component(component_name)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/elisa/core/plugin_registry.py", line 1048, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.6/dist-packages/twisted/python/reflect.py", line 456, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.6/dist-packages/twisted/python/reflect.py", line 392, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/database/dbus_service.py", line 37, in <module>
    from elisa.plugins.poblesec.music_library import album_cover_retriever
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/poblesec/music_library.py", line 32, in <module>
    from elisa.plugins.poblesec.base.list import GenericListViewMode
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/poblesec/base/list.py", line 23, in <module>
    from elisa.plugins.poblesec.actions import Action
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/poblesec/actions.py", line 26, in <module>
    from elisa.plugins.base.models.image import ImageModel
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/base/models/image.py", line 45, in <module>
    _ = install_translation('base')
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 93, in install_translation
    current_locale = get_current_locale()
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 84, in get_current_locale
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.6/locale.py", line 478, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      service_manager             Jun 01 19:15:10  Creating elisa.plugins.database.dbus_service:DatabaseDBusServiceProvider failed. A full traceback can be found at /tmp/elisa_Ficttk.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 225, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 757, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.6/dist-packages/elisa/core/manager.py", line 101, in load_components_iter
    dfr = plugin_registry.create_component(component_name)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/elisa/core/plugin_registry.py", line 1048, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.6/dist-packages/twisted/python/reflect.py", line 456, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.6/dist-packages/twisted/python/reflect.py", line 392, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/database/media_scanner.py", line 40, in <module>
    from elisa.plugins.database.database_parser import DatabaseParser
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/database/database_parser.py", line 23, in <module>
    from elisa.plugins.database.video_parser import VideoParser
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/database/video_parser.py", line 24, in <module>
    from elisa.plugins.database.models import File, Video, Movie, TVShow, TVSeason, \
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/database/models.py", line 37, in <module>
    _ = install_translation('database')
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 93, in install_translation
    current_locale = get_current_locale()
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 84, in get_current_locale
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.6/locale.py", line 478, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      resource_manager            Jun 01 19:15:10  Creating elisa.plugins.database.media_scanner:MediaScanner failed. A full traceback can be found at /tmp/elisa_GLIOYt.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 225, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 757, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.6/dist-packages/elisa/core/manager.py", line 101, in load_components_iter
    dfr = plugin_registry.create_component(component_name)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/elisa/core/plugin_registry.py", line 1048, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.6/dist-packages/twisted/python/reflect.py", line 456, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.6/dist-packages/twisted/python/reflect.py", line 392, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/flickr/resource_provider.py", line 39, in <module>
    from elisa.plugins.base.models.image import ImageModel
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/base/models/image.py", line 45, in <module>
    _ = install_translation('base')
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 93, in install_translation
    current_locale = get_current_locale()
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 84, in get_current_locale
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.6/locale.py", line 478, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      resource_manager            Jun 01 19:15:10  Creating elisa.plugins.flickr.resource_provider:FlickrResourceProvider failed. A full traceback can be found at /tmp/elisa__SUhOY.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
Failure: exceptions.RuntimeError: hildon not running

WARN  MainThread      service_manager             Jun 01 19:15:10  Creating elisa.plugins.osso.osso_service:OssoService failed. A full traceback can be found at /tmp/elisa_0BAtpI.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 225, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 757, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.6/dist-packages/elisa/core/manager.py", line 101, in load_components_iter
    dfr = plugin_registry.create_component(component_name)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/elisa/core/plugin_registry.py", line 1048, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.6/dist-packages/twisted/python/reflect.py", line 456, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.6/dist-packages/twisted/python/reflect.py", line 392, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/youtube/resource_provider.py", line 34, in <module>
    from elisa.plugins.base.models.image import ImageModel
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/base/models/image.py", line 45, in <module>
    _ = install_translation('base')
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 93, in install_translation
    current_locale = get_current_locale()
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 84, in get_current_locale
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.6/locale.py", line 478, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      resource_manager            Jun 01 19:15:10  Creating elisa.plugins.youtube.resource_provider:YoutubeResourceProvider failed. A full traceback can be found at /tmp/elisa_jcrCMi.txt (elisa/core/manager.py:97)
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 225, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 757, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.6/dist-packages/twisted/internet/task.py", line 251, in _tick
    result = iterator.next()
  File "/usr/lib/python2.6/dist-packages/elisa/core/manager.py", line 101, in load_components_iter
    dfr = plugin_registry.create_component(component_name)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/elisa/core/plugin_registry.py", line 1048, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.6/dist-packages/twisted/python/reflect.py", line 456, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.6/dist-packages/twisted/python/reflect.py", line 392, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/discogs/discogs_resource.py", line 32, in <module>
    from elisa.plugins.base.models.image import ImageModel
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/base/models/image.py", line 45, in <module>
    _ = install_translation('base')
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 93, in install_translation
    current_locale = get_current_locale()
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 84, in get_current_locale
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.6/locale.py", line 478, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG

WARN  MainThread      resource_manager            Jun 01 19:15:10  Creating elisa.plugins.discogs.discogs_resource:DiscogsResource failed. A full traceback can be found at /tmp/elisa_KTQPbK.txt (elisa/core/manager.py:97)
Unhandled error in Deferred:
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 225, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 757, in runUntilCurrent
    call.func(*call.args, **call.kw)
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/pigment/pigment_frontend.py", line 527, in _load_first_controller
    dfr = self.create_controller(controller_path)
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/pigment/pigment_frontend.py", line 161, in create_controller
    dfr = plugin_registry.create_component(controller, config, **kwargs)
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/elisa/core/plugin_registry.py", line 1048, in create_component
    component_class = reflect.namedAny('%s.%s' % (module, klass))
  File "/usr/lib/python2.6/dist-packages/twisted/python/reflect.py", line 456, in namedAny
    topLevelPackage = _importAndCheckStack(trialname)
  File "/usr/lib/python2.6/dist-packages/twisted/python/reflect.py", line 392, in _importAndCheckStack
    return __import__(importName)
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/poblesec/main.py", line 26, in <module>
    from elisa.plugins.base.models.image import ImageModel
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/base/models/image.py", line 45, in <module>
    _ = install_translation('base')
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 93, in install_translation
    current_locale = get_current_locale()
  File "/usr/lib/python2.6/dist-packages/elisa/core/utils/i18n.py", line 84, in get_current_locale
    current_locale = locale.getdefaultlocale()[0]
  File "/usr/lib/python2.6/locale.py", line 478, in getdefaultlocale
    return _parse_localename(localename)
  File "/usr/lib/python2.6/locale.py", line 410, in _parse_localename
    raise ValueError, 'unknown locale: %s' % localename
exceptions.ValueError: unknown locale: en_NG
^CTraceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 185, in run
    self.__run()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/gtk2reactor.py", line 225, in simulate
    self.runUntilCurrent()
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 779, in runUntilCurrent
    self.fireSystemEvent("shutdown")
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 585, in fireSystemEvent
    event.fireEvent()
--- <exception caught here> ---
  File "/usr/lib/python2.6/dist-packages/twisted/internet/base.py", line 368, in fireEvent
    result = callable(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/elisa/core/application.py", line 513, in stop
    dfr = self.interface_controller.stop()
  File "/usr/lib/python2.6/dist-packages/elisa/core/interface_controller.py", line 141, in stop
    dfr = frontend.clean()
  File "/usr/lib/python2.6/dist-packages/elisa/plugins/pigment/pigment_frontend.py", line 666, in clean
    if self.controller:
exceptions.AttributeError: 'PigmentFrontend' object has no attribute 'controller'
Unhandled error in Deferred:
Exception AttributeError: "'NoneType' object has no attribute 'Failure'" in <bound method DebugInfo.__del__ of <twisted.internet.defer.DebugInfo instance at 0xa0e632c>> ignored
kels@kels-laptop:~$ 


```

Notice I had to kill elisa. Aptoncd (for putting downloaded repo debs on cds) has to be killed or crashes after excessive memory consumption

---

### Post by Ekeluo on 2009-07-17
Fixed by changing system language to en_US

---

