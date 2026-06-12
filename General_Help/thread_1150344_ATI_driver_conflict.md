---
title: "ATI driver conflict"
date: 2009-05-06
forum: General Help
---

### Post by U2XS on 2009-05-06
The ATI drivers for my Radeon X1250 were properly configured on my Acer Extensa 4420 laptop when I went to Add/Remove programs and I added an ATI driver package.  Upon reboot, I found that my Ubuntu GUI was non functional.  I have tried the following things to fix this on my own.

1.  I&#8217;ve entered Ubuntu Recovery mode and I&#8217;ve used the "xfix"
2.  In the command line I've tried sudo dpkg-reconfigure xserver-xorg
3.  As per [this tutorial]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/"), I've tried: rm -rf .gnome .gnome2 .gconf .gconfd .metacity
4.  Sudo apt-get remove ubuntu-desktop & Sudo apt-get install ubuntu-desktop

In short I'm stuck.  There isn't a lot of sensitive or important data on this drive, but I would like to learn to *fix problems* in Ubuntu as opposed to constantly reinstalling the OS.

---

### Post by clhsharky on 2009-05-06
Have you tried to boot in [safe mode] to desk top.

---

