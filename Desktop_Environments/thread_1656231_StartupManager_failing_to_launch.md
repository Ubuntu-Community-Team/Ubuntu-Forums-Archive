---
title: "StartupManager failing to launch"
date: 2010-12-30
forum: Desktop Environments
---

### Post by jeff.biggeek02 on 2010-12-30
Does anyone know of some things I can check to find the root cause behind this error?  I pulled startupmanager via apt-get, and I get an error when I try to launch the startupmanager executable from a terminal in Gnome.

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Grub2 detected
Usplash not detected
Splashy not detected
**
GLib-GIO:ERROR:/build/buildd/glib2.0-2.26.0/gio/gdbusconnection.c:2270:initable_init: assertion failed: (connection->initialization_error == NULL)

---

### Post by Krytarik on 2011-01-01
Did you try it via the menu, I guess "System -> Administration"?!

---

### Post by ingeon on 2011-01-22
> Xlib:  extension "RANDR" missing on display ":0.0".
Xlib:  extension "RANDR" missing on display ":0.0".Xlib:  extension "RANDR" missing on display ":0.0".
RandR extension missing
Traceback (most recent call last):
  File "/usr/sbin/startupmanager", line 54, in <module>
    main()
  File "/usr/sbin/startupmanager", line 51, in main
    SumGui()
  File "/usr/share/startupmanager/gtk_frontend.py", line 166, in __init__
    self.resolution = utils.get_resolution()
  File "/usr/lib/pymodules/python2.6/bootconfig/utils.py", line 159, in get_resolution
    return matches.group(1) + 'x' + matches.group(2)
AttributeError: 'NoneType' object has no attribute 'group'


Mine gives me this error. New to this kind of problem. Tried apt-get update/upgrade just in case.

edit: okay, sorry found solution. Nvidia xinerama

---

