---
title: "Using DBus Instead of Bonobo to build a GNOME panel applet"
date: 2009-03-04
forum: Desktop Environments
---

### Post by C-- on 2009-03-04
Ok so I heard gnome is going to deprecate the Bonobo component model when it comes to displaying panel applets and will instead be using Dbus in a future release. Obviously it would be smart then to develop new applets with DBus, especially since for my current project I need to use Java, for which DBus has bindings and Bonobo does not.

When it comes to tutorials and documentation however, writing panel applets with Dbus and Java are pretty much non-existent. In fact the Bonobo ones all look about 5 years old.

I was wondering then if anyone here at least knows a link to an up-to-date tutorial for using Dbus and Java, or just Dbus to get a panel applet working with the current gnome panel that will also work when Bonobo is officially deprecated.

Thanks for all your suggestions.

---

### Post by C-- on 2009-03-05
For reference, I have the following dbus and gnome-panel packages installed:

gnome-panel.i386                         2.16.1-7.el5
gnome-panel-devel.i386                   2.16.1-7.el5          

dbus.i386                                1.1.2-12.el5           installeddbus-devel.i386                 1.1.2-12.el5
dbus-glib.i386                           0.73-8.el5
dbus-glib-devel.i386                     0.73-8.el5
dbus-libs.i386                           1.1.2-12.el5   
dbus-python.i386                         0.70-7.el5   
dbus-x11.i386                            1.1.2-12.el5

I would just like to know if I can use these DBus libraries with at gnome panel 2.16, and if so if there is a tutorial or documentation on how to communicate the GUI from the applet to the panel and signals from the panel back to the applet with DBus and without using Bonobo.

---

### Post by C-- on 2009-03-09
Still haven't been able to find any documentation on this...

---

### Post by Xiao-Feng Li on 2009-06-08
After more searching, I found there are already some panel-applets implemented on top of DBus.  For example: [http://lists.freedesktop.org/archives/dbus/2006-January/003961.html](http://lists.freedesktop.org/archives/dbus/2006-January/003961.html)

---

