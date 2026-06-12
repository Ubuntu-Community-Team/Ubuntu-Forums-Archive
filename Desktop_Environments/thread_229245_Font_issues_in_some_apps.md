---
title: "Font issues in some apps"
date: 2006-08-04
forum: Desktop Environments
---

### Post by speck on 2006-08-04
After a few updates yesterday, I am now having problems with system fonts in a few applications. Specifically, all text in VMWare Player's menus and the save downloaded files dialog in Firefox now shows a series of empty rectanges where the text should be. Is a font missing or corrupted and how do I figure out which one?

---

### Post by persuader on 2006-08-04
I have the same problem using Kubuntu 6.06, after the update to kde 3.5.4 packages many gtk apps works without the anti-aliased fonts (thuderbird synaptic ecc. ).
Any idea?

---

### Post by KevinS on 2006-08-04
I'm also having the same problems.  For me, it happened after the following packages were upgraded, although I have no idea which package is causing the problems. 

(Copied from Synaptic history)

Upgraded the following packages:
eog (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
file-roller (2.14.3-0ubuntu1) to 2.14.4-0ubuntu1
gdm (2.14.9-0ubuntu1) to 2.14.10-0ubuntu1
gnome-accessibility-themes (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnome-applets (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnome-applets-data (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnome-games (1:2.14.2.1-0ubuntu1) to 1:2.14.3-0ubuntu1
gnome-games-data (1:2.14.2.1-0ubuntu1) to 1:2.14.3-0ubuntu1
gnome-menus (2.14.0-0ubuntu1) to 2.14.3-0ubuntu1
gnome-screensaver (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnome-session (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnome-themes (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
gnupg (1.4.2.2-1ubuntu2.1) to 1.4.2.2-1ubuntu2.2
gtk2-engines-clearlooks (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-crux (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-highcontrast (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-industrial (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-lighthouseblue (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-mist (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-pixbuf (2.8.18-0ubuntu2) to 2.8.20-0ubuntu1
gtk2-engines-redmond95 (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-smooth (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
gtk2-engines-thinice (1:2.7.4.is.2.6.9-0ubuntu1) to 1:2.7.4.is.2.6.10-0ubuntu1
ia32-libs-gtk (16) to 16.1
language-pack-en (1:6.06+20060705) to 1:6.06+20060725
language-pack-en-base (1:6.06+20060529) to 1:6.06+20060725
language-pack-gnome-en (1:6.06+20060705) to 1:6.06+20060725
language-pack-gnome-en-base (1:6.06+20060529) to 1:6.06+20060725
libeel2-2 (2.14.1-0ubuntu2) to 2.14.3-0ubuntu1
libeel2-data (2.14.1-0ubuntu2) to 2.14.3-0ubuntu1
libgnome-menu2 (2.14.0-0ubuntu1) to 2.14.3-0ubuntu1
libgtk2.0-0 (2.8.18-0ubuntu2) to 2.8.20-0ubuntu1
libgtk2.0-bin (2.8.18-0ubuntu2) to 2.8.20-0ubuntu1
libgtk2.0-common (2.8.18-0ubuntu2) to 2.8.20-0ubuntu1
libgtk2.0-dev (2.8.18-0ubuntu2) to 2.8.20-0ubuntu1
libnautilus-burn3 (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
libnautilus-extension1 (2.14.1-0ubuntu9) to 2.14.3-0ubuntu1
libtiff-tools (3.7.4-1ubuntu3.1) to 3.7.4-1ubuntu3.2
libtiff4 (3.7.4-1ubuntu3.1) to 3.7.4-1ubuntu3.2
libtotem-plparser1 (1.4.1-0ubuntu4) to 1.4.3-0ubuntu1
linux-headers-2.6.15-26 (2.6.15-26.45) to 2.6.15-26.46
linux-headers-2.6.15-26-amd64-generic (2.6.15-26.45) to 2.6.15-26.46
linux-image-2.6.15-26-amd64-generic (2.6.15-26.45) to 2.6.15-26.46
nautilus (2.14.1-0ubuntu9) to 2.14.3-0ubuntu1
nautilus-cd-burner (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1
nautilus-data (2.14.1-0ubuntu9) to 2.14.3-0ubuntu1
python-gmenu (2.14.0-0ubuntu1) to 2.14.3-0ubuntu1
totem (1.4.1-0ubuntu4) to 1.4.3-0ubuntu1
totem-xine (1.4.1-0ubuntu4) to 1.4.3-0ubuntu1
totem-xine-firefox-plugin (1.4.1-0ubuntu4) to 1.4.3-0ubuntu1
yelp (2.14.2-0ubuntu1) to 2.14.3-0ubuntu1

---

### Post by upnix on 2006-08-04
I also have this problem that popped up after my most recent update.

I'm running on AMD64, and I only see this in Open dialoge boxes for 32-bit apps. 

Which means I really can't use OOo at the moment.

[IMG]http://chris.upnix.org/problem.jpg[/IMG]

---

### Post by KevinS on 2006-08-04
Downgrading ia32-libs-gtk from version 16.1 to version 16 fixed the problem on my system.

Thanks to upnix for narrowing the problem!

---

### Post by struess on 2006-08-04
i'm having the exact same problem with open office (on my amd64 system).  might try rolling back the updates one by one :( 

i blame totem.

---

### Post by struess on 2006-08-04
...and that's that.  downgrading ia32-libs-gtk from 16.1 to 16 solved the problem for me, too.  thanks guys :)

---

### Post by KevinS on 2006-08-04
More information:

   [https://launchpad.net/distros/ubuntu/+source/ia32-libs-gtk/+bug/55058](https://launchpad.net/distros/ubuntu/+source/ia32-libs-gtk/+bug/55058)

---

### Post by flying_icarus on 2006-08-05
Just to add my voice. Same problem, downgrading remedies it. 

Hopefully we'll see less of things like this and like libxine breaking flac support (regarding amarok)... I really didn't expect slip-ups like this on a highly regarded distro, and one so nicely polished in many other aspects. [-X

---

### Post by speck on 2006-08-06
Looks like ia32-libs-gtk 16.2 fixes the problem as well.

Thanks everybody!

---

### Post by struess on 2006-08-09
hooray for ubuntu responsiveness!  

16.2 does indeed fix the problem.

---

