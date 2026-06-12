---
title: "Menu wont work"
date: 2009-05-09
forum: Desktop Environments
---

### Post by su-37 on 2009-05-09
I have recently upgradd to Ubuntu 9.04 and am loving it asides from this. I go into system then administration and the following menus wont work. ie i click on them and nothing appears. They are:  software sources and Hardware drivers. Also when i open the update manager and click on setting nothing comes up. Any help would be much appreciated.

---

### Post by ad_267 on 2009-05-09
What do you get if you open a terminal and run:
```
/usr/bin/jockey-gtk
```
and
```
gksu /usr/bin/software-properties-gtk
```

---

### Post by su-37 on 2009-05-09
Hey when i run the first one i get
james@james-laptop:~$ /usr/bin/jockey-gtk
[Code]
james@james-laptop:~$ /usr/bin/jockey-gtk
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 25, in <module>
    import jockey.ui
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 31, in <module>
    from backend import UnknownHandlerException, PermissionDeniedByPolicy, BackendCrashError, polkit_auth_wrapper, dbus_sync_call_signal_wrapper, Backend, DBUS_BUS_NAME
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 32, in <module>
    import detection, xorg_driver
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 32, in <module>
    import handlers, xorg_driver
  File "/usr/lib/python2.6/dist-packages/jockey/xorg_driver.py", line 21, in <module>
    import XKit.xutils
ImportError: No module named XKit.xutils
[code]



and when i run the second one i get:
[code]
james@james-laptop:~$ /usr/bin/jockey-gtk
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 25, in <module>
    import jockey.ui
  File "/usr/lib/python2.6/dist-packages/jockey/ui.py", line 31, in <module>
    from backend import UnknownHandlerException, PermissionDeniedByPolicy, BackendCrashError, polkit_auth_wrapper, dbus_sync_call_signal_wrapper, Backend, DBUS_BUS_NAME
  File "/usr/lib/python2.6/dist-packages/jockey/backend.py", line 32, in <module>
    import detection, xorg_driver
  File "/usr/lib/python2.6/dist-packages/jockey/detection.py", line 32, in <module>
    import handlers, xorg_driver
  File "/usr/lib/python2.6/dist-packages/jockey/xorg_driver.py", line 21, in <module>
    import XKit.xutils
ImportError: No module named XKit.xutils
james@james-laptop:~$ gksu /usr/bin/software-properties-gtk
  File "/usr/bin/software-properties-gtk", line 44, in <module>
    from softwareproperties.gtk.SoftwarePropertiesGtk import SoftwarePropertiesGtk
ImportError: No module named softwareproperties.gtk.SoftwarePropertiesGtk
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSjames@james-laptop:~$ 
[code]

Hopefully this will help you to help me.

---

### Post by ad_267 on 2009-05-09
Hmm ok it looks like a few python libraries are messed up. Try running:
```
sudo aptitude reinstall python-xkit python-software-properties
``` and see if that helps.

---

### Post by su-37 on 2009-05-09
Ok that did help i can now access the hardware drives but for some reason i still cant access the software channels and when i click on the setting button in the update manager noting happens. But i can now use compiz which is a plus.

---

### Post by ad_267 on 2009-05-09
Try running the command again and see what output you get this time.
```
gksu /usr/bin/software-properties-gtk
```

---

### Post by su-37 on 2009-05-10
I ran the first code and the harware driver section came up

[code] james@james-laptop:~$ /usr/bin/jockey-gtk [code]
and when i rune the second one i get.

[code] james@james-laptop:~$ gksu /usr/bin/software-properties-gtk
Traceback (most recent call last):  File "/usr/bin/software-properties-gtk", line 44, in <module>
    from softwareproperties.gtk.SoftwarePropertiesGtk import SoftwarePropertiesGtk
ImportError: No module named gtk.SoftwarePropertiesGtk
james@james-laptop:~$ [code]

and when i run the code in your previous reply i get:
[code] 
james@james-laptop:~$ gksu /usr/bin/software-properties-gtk
Traceback (most recent call last):  File "/usr/bin/software-properties-gtk", line 44, in <module>
    from softwareproperties.gtk.SoftwarePropertiesGtk import SoftwarePropertiesGtk
ImportError: No module named gtk.SoftwarePropertiesGtk
james@james-laptop:~$ gksu /usr/bin/software-properties-gtk
Traceback (most recent call last):  File "/usr/bin/software-properties-gtk", line 44, in <module>
    from softwareproperties.gtk.SoftwarePropertiesGtk import SoftwarePropertiesGtk
ImportError: No module named gtk.SoftwarePropertiesGtk
james@james-laptop:~$ 

[code]

---

### Post by ad_267 on 2009-05-10
Ok try reinstalling the software-properties-gtk package too, I missed that one before.
```
sudo aptitude reinstall software-properties-gtk
```

---

### Post by su-37 on 2009-05-10
Thanks a lot that solved it! Its now working beautifully!  Thanks for the help.

---

