---
title: "Legacy environment"
date: 2015-09-25
forum: Desktop Environments
---

### Post by Tichun on 2015-09-25
Hello, folks.
I'm looking for environment efficient like gnome/kde 1.0 but that will work nowadays with things like newest libreoffice, firefox etc.
Is there solution or environments like lxde are best this way?
My *overall* idea is to have faster running computer instead of better looking one but preserving functionality.

---

### Post by grahammechanical on 2015-09-25
The developers of all desktop environments and user interfaces have been improving their projects over time. Nothing stands still. In the Ubuntu family we have Ubuntu, Xubuntu, Lubuntu, kubuntu, Ubuntu Gnome, Ubuntu Mate and some specialist family members such as Mythbuntu, Edubuntu and Ubuntu Studio.

So, you have a choice. Best to look at the screenshots on each web site to see what you like.

[http://xubuntu.org/](http://xubuntu.org/)

[http://lubuntu.net/](http://lubuntu.net/)

[http://www.kubuntu.org/](http://www.kubuntu.org/)

[https://ubuntugnome.org/](https://ubuntugnome.org/)

[https://ubuntu-mate.org/](https://ubuntu-mate.org/)

Regards.

---

### Post by tgalati4 on 2015-09-25
MATE runs well on older hardware and has all the gnome2 goodness that you are probably familiar with.  I would start with that and see how your system runs.

---

### Post by buzzingrobot on 2015-09-27
An "environment" is generally considered something that manages the windows on the display *and* provides a batch of applications and support libraries. 

A pretty large number of "windows managers" are also in use and these provide only management of applications windows. Search for "Linux window managers" and you find many results. Some are very spartan and idiosyncratic, some are old and not being maintained, and some are actively supported and popular. (Openbox used in LXDE is one of the more widely know windows managers.)

Any application that has dependencies on an environment like KDE or Gnome will pull in those dependencies. So, if you're using a barebones little window manager and install, say, Digikam, you're going to pull in a lot of Digikam's KDE dependencies. (That's really a storage space issue more than it is a speed issue. Code sitting on the drive won't affect perceived speed until something needs to start loading and using it.)

If it's something that is self-contained, like Firefox, then I suspect the only issues you might have would center around theming.

(There's a "Trinity" project that's, I believe, based on old KDE3.  Dunno know if it's available for Ubuntu, though.  Gnome 2 died, went to fork purgatory, and came out as Mate.)

---

