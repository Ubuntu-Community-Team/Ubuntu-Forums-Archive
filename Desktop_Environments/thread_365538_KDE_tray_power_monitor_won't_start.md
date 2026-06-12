---
title: "KDE tray power monitor won't start"
date: 2007-02-19
forum: Desktop Environments
---

### Post by Mr. Sinister on 2007-02-19
After a recent update, the guidance-power-manager.py script won't start. I get the following error message. Does anybody know what might be wrong? The powersaved daemon is running, and I can access all the power info through /proc.

```
/usr/share/python-support/kde-guidance/guidance-power-manager.py
Introspect error: The name org.freedesktop.Hal was not provided by any .service files
Traceback (most recent call last):
  File "/usr/share/python-support/kde-guidance/guidance-power-manager.py", line 740, in ?
    mainWindow = PowermanagerApp(None, "main window")
  File "/usr/share/python-support/kde-guidance/guidance-power-manager.py", line 688, in __init__
    self.pmwidget = PowerManager(self,name)
  File "/usr/share/python-support/kde-guidance/guidance-power-manager.py", line 95, in __init__
    self.powermanager = PowerManage()
  File "/usr/share/python-support/kde-guidance/powermanage.py", line 85, in __init__
    self._initBrightness()
  File "/usr/share/python-support/kde-guidance/powermanage.py", line 233, in _initBrightness
    brightnessDevice = self.hal_manager.FindDeviceByCapability("laptop_panel")
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 25, in __call__
    ret = self._proxy_method (*args, **keywords)
  File "/var/lib/python-support/python2.4/dbus/proxies.py", line 102, in __call__
    reply_message = self._connection.send_with_reply_and_block(message, timeout)
  File "dbus_bindings.pyx", line 455, in dbus_bindings.Connection.send_with_reply_and_block
dbus_bindings.DBusException: The name org.freedesktop.Hal was not provided by any .service files
power-manager: ERROR: Communication problem with power-manager, it probably crashed.

```

---

