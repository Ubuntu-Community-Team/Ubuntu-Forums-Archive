---
title: "MenuLibre and xfce on Ubuntu Studio 17.04"
date: 2017-08-05
forum: Desktop Environments
---

### Post by steveredshaw on 2017-08-05
I am struggling making the Menu Editor work. I get the following terminal message when I run it.

```
/usr/lib/python3/dist-packages/menulibre/MenuEditor.py:30: PyGIWarning: GMenu was imported without specifying a version first. Use gi.require_version('GMenu', '3.0') before import to ensure that the right version gets loaded.  from gi.repository import GdkPixbuf, Gio, GLib, GMenu, Gtk
```

I have tried to insert gi.require_version('GMenu', '3.0') into the MenuEditor.py file (from gi.require_version('GMenu', '3.0')), however that prevents Menu Editor from running altogether.

The Help documentation for Menu Editor does not teach how to use the program. It seems to be fairly intuitive, but I can't get it to change or add to my Whisker menu, so I assume it must be something to do with this errpr report that I am getting.

Any help greatly appreciated....

---

### Post by #&amp;thj^% on 2017-08-05
I just use "menulibre" works well enough for me>
```
apt policy menulibre
menulibre:
  Installed: 2.1.3-0ubuntu1
  Candidate: 2.1.3-0ubuntu1
  Version table:
 *** 2.1.3-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu artful/universe amd64 Packages
        500 http://archive.ubuntu.com/ubuntu artful/universe i386 Packages
        100 /var/lib/dpkg/status

```
EDIT Oops I see now you are using it, Give this a shot to see if any info we can use here to show.
```
menulibre -v
```
Paste back
Also from your menu look in " Accessories > Menu Editor"
Ninj'ed by Dennis N :)

---

### Post by Dennis N on 2017-08-05
Probably best not to run it from a terminal. Using "Menu > Accessories > Menu Editor" will most likely avoid any warnings. I would not call it intuitive. You have to figure out the right steps to add something.

---

### Post by steveredshaw on 2017-08-06
Lots of error information from menulibre -v!!

```
menulibre -v/usr/lib/python3/dist-packages/menulibre/MenuEditor.py:30: PyGIWarning: GMenu was imported without specifying a version first. Use gi.require_version('GMenu', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import GdkPixbuf, Gio, GLib, GMenu, Gtk
DEBUG:menulibre: set_up_logging() 'logging enabled'
DEBUG:menulibre: __init__() 'Using menu: /home/steve/.config/menus/xfce-applications.menu'
DEBUG:menulibre: block() 'Blocking history updates'
DEBUG:menulibre: unblock() 'Unblocking history updates'
DEBUG:menulibre: block() 'Blocking history updates'
DEBUG:menulibre: unblock() 'Unblocking history updates'
DEBUG:menulibre: block() 'Blocking history updates'
DEBUG:menulibre: unblock() 'Unblocking history updates'


(menulibre:5118): Gtk-WARNING **: Allocating size to menulibre+MenulibreApplication+MenulibreWindow 0x558b5ce8a2a0 without calling gtk_widget_get_preferred_width/height(). How does the code know the size to allocate?
DEBUG:menulibre: block() 'Blocking history updates'
DEBUG:menulibre: unblock() 'Unblocking history updates'
[0806/095146.316541:ERROR:browser_gpu_channel_host_factory.cc(103)] Failed to launch GPU process.

```

I renamed this file - /home/steve/.config/menus/xfce-applications.menu - and menu then showed all categories (some of which had mysteriously disappeared recently). However, after running Menu Editor again,  /home/steve/.config/menus/xfce-applications.menu was created again and those categories (Audio production, Graphic design, Video production) have disappeared again!!

More investigation needed, but I'm groping around in the dark at the moment.....

---

### Post by steveredshaw on 2017-08-07
:eek: Well, I have a solution of sorts. Uninstalled Menulibre and installed Alacarte - that has a useful button - Restore System Configuration. That brought back my missing categories.

If anyone is interested, I still get errors reported, similar to the ones I got with Menulibre, but at least my menu is restored and I can add and delete items now.

```
/usr/share/alacarte/Alacarte/MainWindow.py:22: PyGIWarning: GMenu was imported without specifying a version first. Use gi.require_version('GMenu', '3.0') before import to ensure that the right version gets loaded.  from gi.repository import Gtk, GdkPixbuf, Gdk, GMenu


(alacarte:10059): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion 'gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed


(alacarte:10059): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion 'gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed



```

Menulibre seemed to be getting menu settings from various places .config/menus, etc/xdg/... and so on. I tried to alter the 2 xfce-application.menu files that I tracked down on my system, but frankly I don't understand the commands and procedures sufficiently, so probably made things worse.

---

### Post by steveredshaw on 2017-08-08
Even better solution - install Cinnamon desktop - [http://www.omgubuntu.co.uk/2017/05/install-cinnamon-3-4-ubuntu-ppa](http://www.omgubuntu.co.uk/2017/05/install-cinnamon-3-4-ubuntu-ppa)

---

