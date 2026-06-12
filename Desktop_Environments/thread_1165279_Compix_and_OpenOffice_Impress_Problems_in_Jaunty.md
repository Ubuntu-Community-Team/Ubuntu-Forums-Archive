---
title: "Compix and OpenOffice Impress Problems in Jaunty"
date: 2009-05-20
forum: Desktop Environments
---

### Post by rmccarri on 2009-05-20
Hi,
I'm going to be giving a presentation to my department on using Joomla to design web pages.  I would really like to show off the eye candy in Ubuntu during the presentation (in the interest of promoting Open Source software as a whole).

I've installed OpenOffice 3.1 and enabled the openGL transitions for my presentation in Impress.  Also, I will be switching back and forth between desktops, so it would be nice to have Compiz up and running.

Everything is running very smoothly on my laptop with the exception that when I enable Compiz, the Gnome panels are showing up over the top of the slideshow.  Has anyone else come across this problem and found a fix?  Trying to force full screen mode via keyboard shortcuts does not work, unfortunately.
Rob

---

### Post by growled on 2009-05-20
What kind of video card do you have?

---

### Post by rmccarri on 2009-05-20
It's an Intel 945 integrated card.  I've downgraded to the xserver-intel-2.4 drivers to improve the terrible performance issues with Jaunty.

---

### Post by rmccarri on 2009-05-20
Also, I guess that I should note that I have the same problem on my desktop running the the proprietary drivers for nVidia cards, so it doesn't seem to be exclusively an issue with the Intel integrated drivers.

---

### Post by rmccarri on 2009-05-20
Fixed.

There is a fix at the bottom here:

[http://user.services.openoffice.org/en/forum/viewtopic.php?f=10&t=5520](http://user.services.openoffice.org/en/forum/viewtopic.php?f=10&t=5520)

I hadn't noticed that openoffice.org-gnome and openoffice.org-gtk had not been installed after the upgrade to 3.1

Installing these fixed the issue.

---

