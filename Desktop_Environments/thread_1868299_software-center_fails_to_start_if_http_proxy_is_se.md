---
title: "software-center fails to start if http_proxy is set"
date: 2011-10-24
forum: Desktop Environments
---

### Post by vinterkind on 2011-10-24
Hi folks,

I can't start my software-center if the http_proxy or https_proxy environment variable is set.
python is complaining in some sort (saw it while invoking software-center from shell).

```
# software-center
2011-10-24 09:27:20,166 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2011-10-24 09:27:20,248 - softwarecenter.ui.gtk3.app - ERROR - could not initiate dbus
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1116, in setup_dbus_or_bring_other_instance_to_front
    bus = dbus.SessionBus()
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 219, in __new__
    mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 108, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 125, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (software-center:3204): WARNING **: The connection is closed

** (software-center:3204): WARNING **: The connection is closed

** (software-center:3204): WARNING **: Unable to create Ubuntu Menu Proxy: The connection is closed
Traceback (most recent call last):
  File "/usr/bin/software-center", line 151, in <module>
    app = SoftwareCenterAppGtk3(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 317, in __init__
    self.review_loader = get_review_loader(self.cache, self.db)
  File "/usr/share/software-center/softwarecenter/backend/reviews.py", line 1044, in get_review_loader
    review_loader = ReviewLoaderSpawningRNRClient(cache, db)
  File "/usr/share/software-center/softwarecenter/backend/reviews.py", line 652, in __init__
    self.rnrclient = RatingsAndReviewsAPI(cachedir=cachedir)
  File "/usr/lib/python2.7/dist-packages/piston_mini_client/__init__.py", line 251, in __init__
    self._http[scheme] = self._get_http_obj_for_scheme(scheme)
  File "/usr/lib/python2.7/dist-packages/piston_mini_client/__init__.py", line 256, in _get_http_obj_for_scheme
    proxy_info = self._get_proxy_info(scheme)
  File "/usr/lib/python2.7/dist-packages/piston_mini_client/__init__.py", line 281, in _get_proxy_info
    port = int(port)
ValueError: invalid literal for int() with base 10: '8080" '
```

if unset it does work as usual except the missing connection to load the packages ... d'oh!

any help appreciated.

---

