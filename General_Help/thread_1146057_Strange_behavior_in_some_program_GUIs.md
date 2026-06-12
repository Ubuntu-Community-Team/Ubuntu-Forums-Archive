---
title: "Strange behavior in some program GUIs"
date: 2009-05-02
forum: General Help
---

### Post by Sigurd Suhm on 2009-05-02
Hello everyone

I'm having some problems with the GUIs in some of my programs. I first experienced it with OpenOffice.org and it has been consistent with any version I tried installing. Lately I've seen the same behaviour in a few other programs, and I've been trying to find the common source. Testing a few applications I noticed some of the same things in Nethack (X11 version) and also in the Robots standard Gnome game. I think I had similar issues using KDevelop actually.

The Problem:
It seems like elements in my interfaces are randomly disappearing. Especially text and icons on buttons and such in OpenOffice. The actual elements are still there and whenever I move the window everything will show correctly for a while again. In the games parts of the screen would just kinda disappear until I moved the window again.

The issues have really been bugging me. It seems like a standard GUI bug like a missing driver or component or something but I can't seem to find the source. Has anyone else experienced similar issues or does anyone have any suggestions to a solution?

I'm running Ubuntu 9.04 with a pretty basic graphical setup. My GPU is a nVidia 8400GS and I'm using the 180 driver.

Thanks in advance
Sigurd

---

### Post by soro2005 on 2009-05-02
It sounds like it's not the programs but your graphics driver. Try switching off Desktop Effects, and I'm sure you won't see the same behavior. Perhaps it helps if you use [https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://edge.launchpad.net/~ubuntu-x-swat/+archive/x-updates) for your graphics driver. But mind, this is likely going to be more unstable than the drivers in the official repo.

---

### Post by waffen on 2009-08-10
> **Sigurd Suhm said:**
> Hello everyone

I'm having some problems with the GUIs in some of my programs. I first experienced it with OpenOffice.org and it has been consistent with any version I tried installing. Lately I've seen the same behaviour in a few other programs, and I've been trying to find the common source. Testing a few applications I noticed some of the same things in Nethack (X11 version) and also in the Robots standard Gnome game. I think I had similar issues using KDevelop actually.

The Problem:
It seems like elements in my interfaces are randomly disappearing. Especially text and icons on buttons and such in OpenOffice. The actual elements are still there and whenever I move the window everything will show correctly for a while again. In the games parts of the screen would just kinda disappear until I moved the window again.

The issues have really been bugging me. It seems like a standard GUI bug like a missing driver or component or something but I can't seem to find the source. Has anyone else experienced similar issues or does anyone have any suggestions to a solution?

I'm running Ubuntu 9.04 with a pretty basic graphical setup. My GPU is a nVidia 8400GS and I'm using the 180 driver.

Thanks in advance
Sigurd

Hello,

I have the SAME odd issues but only with Openoffice.
I just discover when I reinstall from zero Ooo: I forget reinstall openoffice.org-gtk and the openoffice.org-gnome packages so when I click in Ooo I see and blue theme and very fast startup for it, I cant see any problem with the buttons or selected zones (disapears, I need move the OOo screnn to show again or scroll with the mouse) but I cant the quickstart icon in the tray, so I'll go to resintall these packages and the problems comeback! ](*,)](*,)

So I think these packages are the problem, but I only have these problems only with Ooo I dont play games (yet! ;-) ) in mi laptop.

I use Compiz and have the same NVidia driver 180.44 my card is a Quadro NVS 135M with 256MB RAM...

I'll try with the repos sended in the other post.. please post if you have any succes or not with that(if you instelled them) or if you found any solution for the problem.

Thanks in advance!

Mario

---

