---
title: "Compiz on Sid"
date: 2008-04-18
forum: Desktop Effects &amp; Customization
---

### Post by user@righthere on 2008-04-18
Hi,

I did a safe-upgrade to sid from lenny and tried running compiz, having installed practically every compiz / compuz fusion related package I could see in synaptic. I also installed xserver-xorg and libgl1-mesa-dri, following the Deb wiki. When I ran compiz --replace, the results were quite funny.

sanjeev@thingy:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 00:02.0 0300: 8086:2562 (rev 03) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present.
Checking for FBConfig: present.
Checking for Xgl: not present.
Starting kde-window-decorator
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'

Compiz ran, but I suddenly had 16 desktops in my preview area and my comp had slowed down considerably. I'm looking to correct the 'errors' displayed. Any ideas? It worked way better on Gnome.

---

### Post by Eclipse. on 2008-04-18
Disable the dbus plugin.

---

### Post by Zorael on 2008-04-18
Add the argument **--ignore-desktop-hints** when using Compiz with KDE. KDE uses viewports and Compiz workspaces. Stuff goes wrong, you get 4x4 desktops instead of a cube.

> Both viewports and workspaces are a way of configuring virtual desktops.
[list]
    [*]A "workspace" is one of several complete independent virtual desktops
    [*]A "viewport" is a screen-sized portion of a virtual desktop which can be much larger than your physical screen.[/list]
In practice, the major difference is that windows can span viewport boundaries, but not workspace boundaries. Apparently this is confusing behavior for many people, so the GNOME folks have decided to get rid of viewports. However, viewport-spanning can be a very useful feature, particularly if you ever have to deal with files containing really long lines and want to stretch some Xterms out to 400 character line lengths...
[Source](http://www.astro.ucla.edu/~mperrin/OLD/gnomeviewports.html)


Anyway, add the argument and hopefully things will get sane again.

edit: You may also want to install emerald and have Compiz run it instead of kde-window-decorator. At least the one included in the Gutsy package (which likely differs from yours) [is buggy](https://bugs.launchpad.net/compiz/+bug/129801).

---

