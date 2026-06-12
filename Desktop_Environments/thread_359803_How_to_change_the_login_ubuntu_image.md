---
title: "How to change the login ubuntu image?"
date: 2007-02-12
forum: Desktop Environments
---

### Post by shareMenaPeace on 2007-02-12
Hi,
how can i find out the name and location of this attached image. I want to remove or exchange it.

It has nothing todo with the usplash.

Ideas? Thx

---

### Post by Paerez on 2007-02-12
it is in /usr/share/pixmaps/splash. The default is "ubuntu-splash.png"

---

### Post by shareMenaPeace on 2007-02-12
Thx i will just overwrite it...

---

### Post by Paerez on 2007-02-12
the better thing to do is put a splash into the folder and change the link. "ubuntu-splash.png" is by default a link to "ubuntu-slick.png". I put another one in my directory and changed the link.

---

### Post by shareMenaPeace on 2007-02-12
What you mean, where can i change the link - the folder just contains png images.
Those
gnome-splash.png  ubuntu-slick.png  ubuntu-smooth.png  ubuntu-splash.png

---

### Post by Paerez on 2007-02-12
if you look closely at ubuntu-splash.png, it has a little arrow on it since it is a link.

I only know how to do this on the terminal, but first your put your splash in the folder (lets call it mysplash.png), then do this:
```
cd /usr/share/pixmaps/splash
sudo ln -sf mysplash.png ubuntu-splash.png
```

which makes ubuntu-splash.png point to mysplash.png.

Then you can keep a whole bunch of splashes in the folder and just switch the links to change it. Or you can just overwrite it :D

---

### Post by shareMenaPeace on 2007-02-12
Cool thanks, i just changed it and it works very well - it is much faster now too.

---

### Post by CowzRule on 2007-02-12
Try this```
sudo aptitude install gnome-splashscreen-manager
```

---

### Post by shareMenaPeace on 2007-02-12
Thx, i installed and run it but it doesnt show any allready existing splashscreens.
Maybe i need to reboot?

And these errors.
> /usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_param_spec_boxed: assertion `G_TYPE_IS_BOXED (boxed_type)' failed
/usr/lib/ruby/1.8/glib2.rb: line 55
   GLib-GObject-CRITICAL **:g_object_class_install_property: assertion `G_IS_PARAM_SPEC (pspec)' failed
Create SplashScreen-File


---

