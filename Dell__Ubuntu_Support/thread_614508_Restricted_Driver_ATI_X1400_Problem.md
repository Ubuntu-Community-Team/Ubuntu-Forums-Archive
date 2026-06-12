---
title: "Restricted Driver ATI X1400 Problem"
date: 2007-11-16
forum: Dell  Ubuntu Support
---

### Post by DeusExodos on 2007-11-16
Hello,

I just reinstalled Ubuntu so I could get Gutsy. On the previous version, my video card was recognized right away by the restricted drivers. (I have an ATI Mobility Radeon X1400) When I go to the restricted drivers it says that the ATI accelerated graphics driver is not in use. When it select it for use, I get this error:

The software source for the package

   xorg-driver-fglrx

 is not enabled.

Please help,

Pedro

---

### Post by wlc3069 on 2007-11-16
i had a similar problem all i did was type into the terminal
sudo apt-get install xorg-driver-fglrx

hopefully that helps

---

### Post by DeusExodos on 2007-11-16
hey that actually work really well. 
Thanks!

---

### Post by BenLi on 2007-12-13
I have the same problem but here's what it says:

ben@ben-laptop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xorg-driver-fglrx
ben@ben-laptop:~$ 


Help Please?

---

### Post by ::Lagro on 2007-12-14
Be sure all your repositories are enabled!

---

### Post by erfahren on 2007-12-14
> **::Lagro said:**
> Be sure all your repositories are enabled!
yeah, when Gutsy is installed and no internet connection is present the repositories are commented out in /etc/apt/sources.list.

that didn't happen in previous versions and seems to be causing alot of confusion.

-- ATI card users - don't forget to install xserver-xgl and restart X (ctrl+Alt+Backspace) to be able to enable desktop effects!

---

