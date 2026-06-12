---
title: "Gtk/Qt problem"
date: 2012-03-16
forum: Desktop Environments
---

### Post by mogeb on 2012-03-16
Hi,
I am developping a software using Qt 4.7. When I try to run on Ubuntu 11.10 64 bits (Unity), i get the following error:
(The_Application_Name.bin:25985): Gtk-CRITICAL **: IA__gtk_widget_style_get: assertion `GTK_IS_WIDGET (widget)' failed

If I install the package kde-full and log into a KDE session, the application works properly (I guess because KDE is written in Qt, am I right?)

I tried everyting:
I installed the packages libqt4-core, -gui, -network, -xml, -xmlpattern
I tried using LD_PRELOAD to preload all the Qt libraries needed
I tried installing all sort of packages related to Gtk and Qt yet nothing works.

Any help would be appreciated. Even if you could just explan to me the error I am getting and why.
Thank you!

---

