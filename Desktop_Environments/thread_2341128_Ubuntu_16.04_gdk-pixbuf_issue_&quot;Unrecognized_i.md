---
title: "Ubuntu 16.04 gdk-pixbuf issue &quot;Unrecognized image file format&quot;"
date: 2016-10-25
forum: Desktop Environments
---

### Post by bla- on 2016-10-25
Hello everyone,
I'm struggling with a gdk-pixbuf issue. Unity will segfault on start, I can manually start xfwm4. But GTK applications either crash or  start without icons and many error messages such as "Gtk-WARNING **: Error loading theme icon 'gtk-convert' for stock: Unrecognized image file format". Looking at the syslog reveal error messages such as "Oct 25 10:14:23 xxxxx gnome-session[29961]: (nm-applet:30339): Gtk-WARNING **: Error loading image 'file:///usr/share/themes/Ambiance/gtk-3.0/assets/entry.png': Unrecognized image file format
Oct 25 10:14:23 xxxxx gnome-session[29961]: (nm-applet:30339): Gtk-WARNING **: Error loading image 'file:///usr/share/themes/Ambiance/gtk-3.0/assets/entry-disabled.png': Unrecognized image file format" 

The files are there and valid pngs. SVGs also do not work. I tried to reinstall gdk-pixbuf,libpng* but it didn't help. I also tried to update the mime database and regenerate gdk-pixbuffer loaders.cache.
Any hint what might be wrong or how to debug this?
Thanks!
Jan

---

### Post by mc4man on 2016-10-25
No real clue but if you're mixing DE's then generally a poor idea. Just to see what's this report?
```
dpkg -l | grep libglib
```

---

### Post by bla- on 2016-10-26
I'm not mixing desktop enviroments, I normally run regular unity. Running xfwm4 was just a quick test to check if x is completely broken or if it is just unity.

Here is the output from dpkg:
> [FONT=courier new]ii  libglib2.0-0:amd64                                    2.48.1-1~ubuntu16.04.1                        amd64        GLib library of C routines
ii  libglib2.0-0:i386                                     2.48.1-1~ubuntu16.04.1                        i386         GLib library of C routines
ii  libglib2.0-bin                                        2.48.1-1~ubuntu16.04.1                        amd64        Programs for the GLib library
ii  libglib2.0-data                                       2.48.1-1~ubuntu16.04.1                        all          Common files for GLib library
ii  libglib2.0-dev                                        2.48.1-1~ubuntu16.04.1                        amd64        Development files for the GLib library
ii  libglib2.0-doc                                        2.48.1-1~ubuntu16.04.1                        all          Documentation files for the GLib library
rc  libglibmm-2.4-1c2a:amd64                              2.39.93-0ubuntu1                              amd64        C++ wrapper for the GLib toolkit (shared libraries)
ii  libglibmm-2.4-1v5:amd64                               2.46.3-1                                      amd64        C++ wrapper for the GLib toolkit (shared libraries)[/FONT]

---

### Post by bla- on 2016-10-26
Issue solved. Missing read permissions in /usr/share/mime. Was likely caused by a buggy closed source installer

---

