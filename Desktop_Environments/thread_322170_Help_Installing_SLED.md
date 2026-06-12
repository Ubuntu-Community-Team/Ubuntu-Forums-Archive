---
title: "Help Installing SLED"
date: 2006-12-20
forum: Desktop Environments
---

### Post by nami on 2006-12-20
I found the following link which talks about The SLED's menu,  I downloaded the deb files and installed all the dependencies listed on the first post of that thread.

[http://www.ubuntuforums.org/showthread.php?t=208131&page=5&highlight=sled](http://www.ubuntuforums.org/showthread.php?t=208131&page=5&highlight=sled)

When I double click on the deb files, they will not install.  How do I install this menu?

Any help will be appreciated, even if its a link on how to do it.

---

### Post by whoismilan on 2006-12-20
Do you get an error message of some sort?

First the file is a *deb.gz (gnome-main-menu_0.6.1ubuntu3_i386.deb.gz, if this is the one you downloaded), which is a comressed archive. Right-click, choose "Extract Here". Then you will get a *.deb file. Double-click this, and GDebi Package Installer should open, then press "Install Package" (if GDebi Package Installer does not open when double-clicking, right-click and choose "Open with "GDebi Package Installer"").

---

### Post by nami on 2006-12-23
It's ok, I got it installed by doing:

> sudo apt-get install gnome-main-menu

But it looks different from some of the screenshots I have seen.  I seem to have to click on the button to get the search up.  In the screenshots the search is already there.

How do I get the search visible at the top or the bottom?

[IMG]http://img297.imageshack.us/img297/8258/dsc00847bm4.jpg[/IMG]

---

### Post by blackmh on 2006-12-23
One tip; to capture desktop screenshot with delay type in console
 "gnome-screenshot --delay=x"  (where x=number of seconds) if you want to take ss with delay. No need for camera next time :)

---

### Post by nami on 2006-12-24
> **blackmh said:**
> One tip; to capture desktop screenshot with delay type in console
 "gnome-screenshot --delay=x"  (where x=number of seconds) if you want to take ss with delay. No need for camera next time :)

SWEET! :D

---

### Post by xopher on 2006-12-24
> How do I get the search visible at the top or the bottom?

The version in the repositories is probably older than the one you've compared screenshots with.

So if you don't find a deb anywhere, you might have to compile it yourself.

This is just a guess though, so remember the Christmas spirit if I'm wrong ;)

---

