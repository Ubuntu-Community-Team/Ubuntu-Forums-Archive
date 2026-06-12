---
title: "Onboard (onscreen keyboard) not working."
date: 2017-02-16
forum: Desktop Environments
---

### Post by qwagmire2 on 2017-02-16
Ubuntu 16.04
HP Elitebook 2760p  

I cannot get the onscreen keyboard to come up. I already turned it on in the Universal Access settings. I also opened up Onboard settings to have it auto hide at the bottom of the screen. When I tried to get it running from terminal, it got.

```
Traceback (most recent call last):
  File "/usr/bin/onboard", line 36, in <module>
    ob = Onboard()
  File "/usr/lib/python3/dist-packages/Onboard/OnboardGtk.py", line 140, in __init__
    remote.Show(dbus_interface=ServiceOnboardKeyboard.IFACE)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.UnknownMethod: Method "Show" with signature "" on interface "org.onboard.Onboard.Keyboard" doesn't exist
 
```

I am also unable to get finger touch enabled, though the stylus input seems to be working fine. Any ideas?

---

