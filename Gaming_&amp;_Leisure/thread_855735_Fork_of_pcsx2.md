---
title: "Fork of pcsx2?"
date: 2008-07-10
forum: Gaming &amp; Leisure
---

### Post by devfil on 2008-07-10
pcsx2 support for linux isn't good and is impossible to make a deb package for it because there are some issues about license and some problems with linux code. Some upstreams ignore all linux support request and only say to use windows to play pcsx2 (WTF!), others are away from years.
So I think it is necessary to make a fork of pcsx2 for linux to make it *working* as it should and to make it to use all what linux can offer (faster gameplay, more stability, etc...).
Now I want to know, what do you think about this idea?

---

### Post by tjwoosta on 2008-07-11
> pcsx2 support for linux isn't good and is impossible to make a deb package for it because there are some issues about license and some problems with linux code

thats not true

i downlaoded the .deb for hardy 64bit from getdeb.net just the other day  (it all works fine but my system cant handle it)

link
[http://www.getdeb.net/category.php?id=3]("http://www.getdeb.net/category.php?id=3")

---

### Post by devfil on 2008-07-11
getdeb doesn't respect the policy for the packages. Is impossible to make an *official* package of it.
For example all the config dir of pcsx2 are installed in the same dir of the binary (/usr/bin) when they should be put in ~/.pcsx/
To write in /usr/bin dir you will need the superuser privileges, so config dir cannot be used.
The binary must be installed in /usr/bin as explained in Filesystem Hierarchy Standard document.
All the sources files *must* contain on header a copy of the license adopted.

---

### Post by barius on 2008-07-12
That's just the way the .deb was created, there is nothing preventing you from making a package that creates ~/.pcsx2 and configures the program to use it.

---

### Post by devfil on 2008-07-12
> **barius said:**
> That's just the way the .deb was created, there is nothing preventing you from making a package that creates ~/.pcsx2 and configures the program to use it.

The .deb package doesn't follow the Debian policy for package, so it will not be included in Debian and Ubuntu. Also the .deb doesn't work properly, for example it doesn't load the pcsx2 image.
However pcsx2 doesn't build in Intrepid Ibex,

---

### Post by disturbedite on 2008-07-12
> **devfil said:**
> The .deb package doesn't follow the Debian policy for package, so it will not be included in Debian and Ubuntu. Also the .deb doesn't work properly, for example it doesn't load the pcsx2 image.
However pcsx2 doesn't build in Intrepid Ibex,
this is more of a glitch than a bug, per se. iirc, i noticed this "issue" and with minimal research on my own system i found the pcsx2 icon was actually included in the package. the problem is that pcsx2's .desktop file looks for a .xpm image for the icon. but the icon shipped with pcsx2 is a png file. so all one has to do to rectify the issue to rename the .xpm field in the .desktop file to .png.
or set the correct icon via one's menu editor.

---

### Post by devfil on 2008-07-13
> **disturbedite said:**
> this is more of a glitch than a bug, per se. iirc, i noticed this "issue" and with minimal research on my own system i found the pcsx2 icon was actually included in the package. the problem is that pcsx2's .desktop file looks for a .xpm image for the icon. but the icon shipped with pcsx2 is a png file. so all one has to do to rectify the issue to rename the .xpm field in the .desktop file to .png.
or set the correct icon via one's menu editor.

You didn't understand.
The pcsx2 image not loaded is:
** (<unknown>:7797): WARNING **: Couldn't find pixmap file: pcsxAbout.bmp

However a fork is necessary to optimize pcsx2 on linux.

---

