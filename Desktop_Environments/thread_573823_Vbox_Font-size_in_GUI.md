---
title: "Vbox Font-size in GUI"
date: 2007-10-12
forum: Desktop Environments
---

### Post by Helmi on 2007-10-12
Hi,

i did a fresh install yesterday and after installing VirtualBox (via the repos) i wonder about the big font size.

To give you an idea how big it is, i opened envy next to it and did a shot. Envy's font size is the size that all the rest of the system has. VBox is about double to triple the size.

[ATTACH]46097[/ATTACH]

---

### Post by depi on 2007-10-20
I have the same problem after I've installed Ubuntu 7.10

---

### Post by miggols99 on 2007-10-20
It's a Qt app, so it won't integrate too well with Gtk apps. try 'qtconfig'. You can change the font size there.

---

### Post by kar0puz on 2007-10-23
Hi,

Take a look at  [https://bugs.launchpad.net/ubuntu/+source/qt-x11-free/+bug/145709]("https://bugs.launchpad.net/ubuntu/+source/qt-x11-free/+bug/145709")
worked just fine for me.

---

