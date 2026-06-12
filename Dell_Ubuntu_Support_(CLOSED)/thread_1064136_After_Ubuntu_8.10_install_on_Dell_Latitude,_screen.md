---
title: "After Ubuntu 8.10 install on Dell Latitude, screen resolution is fouled"
date: 2009-02-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by edhawk2 on 2009-02-08
I installed Ubuntu 8.10 on my Latitude laptop and since then the screen resolution has been changed.  On boot up, the text characters are larger than before and I can't change screen resolution at all while running Ubuntu.  I think the installation may have screwed up the bios.  

Any thoughts?

---

### Post by utnubuuser on 2009-02-08
Hi - That's most likely a driver issue, - not Bios.  Check System>>Administration>>Hardware Drivers.

You probably need the fglrx driver, since most Latitude's have ATI graphics cards.

You might want to post the output of > dmesg and/or > lspci from a terminal, so anyone stopping by can see what your hardware is.

One of the simplest commands to see if xorg will correct the problem without a different driver is:> sudo dpkg-reconfigure xserver-xorg

---

### Post by iris-n on 2009-02-09
My Latitude has an integrated intel i810 graphics card. 

I've ran into this problem to. To solve it, I had to System->Preferences->Main Menu. Then Other->Screens and Graphics. Then I was able to change resolution. There is also System->Preferences->Screen Resolution, but for some reason I remember that that didn't worked.

Hope that helps,

Iris

---

