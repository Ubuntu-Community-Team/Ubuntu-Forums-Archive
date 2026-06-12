---
title: "ibex/window maker/WorkspaceSpecificBack"
date: 2009-04-18
forum: Desktop Environments
---

### Post by rick71 on 2009-04-18
Today I upgraded my Hardy install to Ibex. Windowmaker started crashing on login. I then did a clean Ibex install. Windowmaker still crashed. I narrowed it down to the WorkspaceSpecificBack bug. In later builds of .92, windowmaker crashes if WorkspaceSpecificBack is used in the main config file. Has anyone found a fix/workaround for this?

---

### Post by Gardnerman on 2009-04-21
I got bitten by this recently, too. I found a reference to a fix at [https://qa.mandriva.com/show_bug.cgi?id=25602](https://qa.mandriva.com/show_bug.cgi?id=25602), but have been unable to find the relevant source so far.

---

### Post by rick71 on 2009-04-21
Hardy uses 0.92.0-7ubuntu1. Ibex uses 0.92.0-7ubuntu10. I have no idea what the differences are.

I used  version 0.92.0-7 in PCLOS 2007, which was actually from and older PCLOS release. The wmaker in PCLOS 2007 had the WorkspaceSpecificBack bug. When I upgraded to PCLOS 2009, I kept 0.92.0-7.

I remember trying to compile WindowMaker, but I don't think I was successful, since I am still using that old version in PCLOS.

I use Ubuntu at work, and I'd really like to get WindowMaker working. I very much like the different wallpapers on different desktops, and and the availability of custom mouse buttons allowing me to have custom menus when I click on the desktop.

The referenced Mandriva build is 0.92.0-10, and I haven't found a -10 release, either. The tar releases at windowmaker.info doesn't seem to be numbered with -7 or -10.

---

### Post by hyperdude111 on 2009-04-21
Dont bother with ibex, jaunty is out within the next 2 days just try that.

---

### Post by rick71 on 2009-04-21
It appears Jaunty will use the same version as Ibex.

---

### Post by rick71 on 2009-04-21
I downloaded the latest WindowMaker source, and tried to compile. I can't find the appropriate X11 headers and dev files, so I can't compile. here's the error I'm getting:

checking for X... no
configure: error: The path for the X11 files not found!
Make sure you have X and it's headers and libraries (the -devel packages
in Linux) installed.

I don't see any more X11 or xorg dev packages to install.

---

### Post by rick71 on 2009-04-23
I have reported the bug at launchpad.

---

### Post by rick71 on 2009-04-24
I've installed Jaunty in a VM for testing. The version of WindowMaker that comes with Jaunty also suffers from the WorkspaceSpecificBack bug.

---

