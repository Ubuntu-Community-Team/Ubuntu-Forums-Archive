---
title: "Setting up CUSTOM Screen Resolution?"
date: 2011-03-18
forum: Desktop Environments
---

### Post by fight2survive on 2011-03-18
I have ubuntu 10.10 installed on my computer in dual boot with windows 7, but i am using a 27-inches Samsung screen through an hdmi cable to connect my computer. whenever i try getting on ubuntu, i cannot see the top and bottom of the desktop (so i cant access the menu bar or anything!)
(while using my spare vga cable) i tried downloading the nvidia driver & utility for my video card (gtx 460), but even using that, i could not setup my screen resolution manually. 
When i setup my windows, i was able to manually setup a custom resolution (i.e. 1842x1026) through the nvidia utility to be able to get the screen the fit properly.

I was wondering if there is any way i could do the same for ubuntu, perhaps through terminal...
thanks!

---

### Post by fight2survive on 2011-03-18
bump! really need help with this please!

---

### Post by fight2survive on 2011-03-19
please help i cannot change my resolution from 680x480 and it is VERY frustrating.

---

### Post by celldweller1591 on 2011-03-19
Try this if you are suing VGA.  
> xrandr --output VGA --mode 1600x900 --rate 75
you can replace 1600x900 to any desired resolution. I have an HD LED Monitor 20" and it works fine with the above setting with small changes :)

---

### Post by fight2survive on 2011-03-19
the thing is i cannot use my vga output because of my video card, i can only use either the dvi or mini-HDMI output. i still tried this and it gives me "xrandr: Failed to get size of gamma for output default
warning: output VGA not found; ignoring"
???:confused:

---

### Post by fight2survive on 2011-03-19
(preferrably the dvi output)

---

### Post by Krytarik on 2011-03-19
Is this an actual TV screen? If so, try modifying its input options. I did have those issue with one, and solved it this way.

If not or if that doesn't work, try following this guide:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

---

