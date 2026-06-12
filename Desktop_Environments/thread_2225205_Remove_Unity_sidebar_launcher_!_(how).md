---
title: "Remove Unity sidebar launcher ?!? (how?)"
date: 2014-05-20
forum: Desktop Environments
---

### Post by Coder88 on 2014-05-20
How can i remove that gawd awful Unity sidebar launcher?!? I just installed Ubuntu desktop 14.04 and as before there is that sidebar launcher that aesthetically I want removed. Ubuntu used to have a gnome desktop with a top left menu to click with drop menus, etc.-- that is what I want back! I installed (synaptic) the Gnome meta package (and chose lightgm) and rebooted but alas still am looking at that unity launcher. Yes I know how to autohide it, but i want that Unity interface gone. If this can not be removed from Ubuntu, then I am done with Ubuntu and will just go to a different distro; also, not being able to remove Unity really goes against the philosophy of linux imho, that of making it what one wants, choosing now the desktop GUI looks and acts. If I simply remove Unity using synaptic, and reboot, would I be stuck with a useless unbootable GUI desktop

---

### Post by philinux on 2014-05-20
Simple. Install the package gnome-session-flashback then logout. From the login screen choose your preferred DE session.

Alternatively there is Lubuntu and Xubuntu.

---

### Post by Frogs Hair on 2014-05-20
Unity is one of many desktop environments available for Ubuntu and has been default since 2011 . Gnome 2  was abandoned by Gnome and forked into the Mate desktop , You can get back a familiar look on your current installation.  [http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html](http://www.webupd8.org/2014/04/how-to-install-and-tweak-gnome.html)

Mate: [http://mate-desktop.org/](http://mate-desktop.org/)

---

### Post by Coder88 on 2014-05-20
Thank you everybody! Solved. That gnome-session-flashback install did the trick.

It would be nice if during the installation of Ubuntu desktop that the install process would ask the user what type of interface s/he wants, e.g. Unity, classic Gnome, KDE, Fluxbox, etc.

---

### Post by deadflowr on 2014-05-20
> **Coder88 said:**
> 
It would be nice if during the installation of Ubuntu desktop that the install process would ask the user what type of interface s/he wants, e.g. Unity, classic Gnome, KDE, Fluxbox, etc.

You can do that with a [mini install]("https://help.ubuntu.com/community/Installation/MinimalCD").

But they are not going to do that with the regular one.

---

### Post by buzzingrobot on 2014-05-21
> **deadflowr said:**
> You can do that with a [mini install]("https://help.ubuntu.com/community/Installation/MinimalCD").

But they are not going to do that with the regular one.

Indeed.  The mini.iso install is equivalent in function to a network install on other distributions.

Contemporary install images have outgrown the space available on CD's, so require either a DVD or a USB stick of sufficient size.

if install images, for Ubuntu or any other distribution, were to contain several alternative interfaces, they would be far too large for DVD's.

OpenSuse, for example, does make available one install image with both Gnome and KDE on it.  It's 4.3 Gb.

---

