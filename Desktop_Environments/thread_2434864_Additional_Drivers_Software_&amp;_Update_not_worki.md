---
title: "Additional Drivers /Software &amp; Update not working"
date: 2020-01-12
forum: Desktop Environments
---

### Post by sarpreet on 2020-01-12
Hello,

I am running :-
Description:    Ubuntu 19.10
Release:    19.10

software-properties-gtk:
  Installed: 0.98.5
  Candidate: 0.98.5
  Version table:
 *** 0.98.5 500
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) eoan/main amd64 Packages
        500 [http://ca.archive.ubuntu.com/ubuntu](http://ca.archive.ubuntu.com/ubuntu) eoan/main i386 Packages
        100 /var/lib/dpkg/status





I am trying to run Additional Drivers /Software & Update . But it opened once and froze and never opened again. 
When I try running the command:-
$ sudo software-properties-gtk

Did a remove and reinstall of the same, but did not work.

It returns:-


ERROR:dbus.proxies:Introspect error on :1.2559:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 100, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 175, in __init__
    self.backend.Reload();
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 72, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 147, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 653, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.2559 was not provided by any .service files


Also, the syslog says:-
name='com.ubuntu.SoftwareProperties' requested by ':1.2455' (uid=1000 pid=2267 comm="/usr/bin/python3 /usr/bin/software-properties-gtk " label="unconfined") (using servicehelper)
Jan 12 11:58:55 gillZ com.ubuntu.SoftwareProperties[2192]: Unable to init server: Could not connect: Connection refused
Jan 12 11:58:55 gillZ com.ubuntu.SoftwareProperties[2192]: Unable to init server: Could not connect: Connection refused
Jan 12 11:58:55 gillZ dbus-daemon[2192]: [system] Successfully activated service 'com.ubuntu.SoftwareProperties'
Jan 12 11:58:55 gillZ com.ubuntu.SoftwareProperties[2192]: Traceback (most recent call last):
Jan 12 11:58:55 gillZ com.ubuntu.SoftwareProperties[2192]:   File "/usr/lib/software-properties/software-properties-dbus", line 68, in <module>
Jan 12 11:58:55 gillZ com.ubuntu.SoftwareProperties[2192]:     server = SoftwarePropertiesDBus(bus, datadir=datadir)
Jan 12 11:58:55 gillZ com.ubuntu.SoftwareProperties[2192]:   File "/lib/python3/dist-packages/softwareproperties/dbus/SoftwarePropertiesDBus.py", line 66, in __init__
Jan 12 11:58:55 gillZ com.ubuntu.SoftwareProperties[2192]:     self._livepatch_service = LivepatchService()
Jan 12 11:58:55 gillZ com.ubuntu.SoftwareProperties[2192]:   File "/lib/python3/dist-packages/softwareproperties/LivepatchService.py", line 93, in __init__
Jan 12 11:58:55 gillZ com.ubuntu.SoftwareProperties[2192]:     self._session = requests_unixsocket.Session()
Jan 12 11:58:55 gillZ com.ubuntu.SoftwareProperties[2192]: NameError: name 'requests_unixsocket' is not defined
Jan 12 11:58:55 gillZ software-properties-drivers.desktop[3536]: ERROR:dbus.proxies:Introspect error on :1.2457:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Jan 12 11:58:55 gillZ software-properties-drivers.desktop[3536]: Traceback (most recent call last):
Jan 12 11:58:55 gillZ software-properties-drivers.desktop[3536]:   File "/usr/bin/software-properties-gtk", line 100, in <module>
Jan 12 11:58:55 gillZ software-properties-drivers.desktop[3536]:     app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
Jan 12 11:58:55 gillZ software-properties-drivers.desktop[3536]:   File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 175, in __init__
Jan 12 11:58:55 gillZ software-properties-drivers.desktop[3536]:     self.backend.Reload();
Jan 12 11:58:55 gillZ software-properties-drivers.desktop[3536]:   File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 72, in __call__
Jan 12 11:58:55 gillZ software-properties-drivers.desktop[3536]:     return self._proxy_method(*args, **keywords)
Jan 12 11:58:55 gillZ software-properties-drivers.desktop[3536]:   File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 147, in __call__
Jan 12 11:58:55 gillZ software-properties-drivers.desktop[3536]:     **keywords)
Jan 12 11:58:55 gillZ software-properties-drivers.desktop[3536]:   File "/usr/lib/python3/dist-packages/dbus/connection.py", line 653, in call_blocking

---

