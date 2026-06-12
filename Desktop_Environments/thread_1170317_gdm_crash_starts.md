---
title: "gdm crash starts"
date: 2009-05-26
forum: Desktop Environments
---

### Post by Saiph on 2009-05-26
After upgrade to kernel 2.6.28.12 Ubuntu give me black screen.
I use gnome, start gdm give me - black screen. No login screen.
I install kde-desktop ... kdm-default ... the same - black screen.
I want my UBUNTU baack!!! Please help :(

Ubuntu is the best :P

---

### Post by zeex on 2009-05-26
> **Saiph said:**
> After upgrade to kernel 2.6.28.12 Ubuntu give me black screen.
I use gnome, start gdm give me - black screen. No login screen.
I install kde-desktop ... kdm-default ... the same - black screen.
I want my UBUNTU baack!!! Please help :(

Ubuntu is the best :P

Hi, 

seems like graphics issue. Just to check if you kept the previous kernel try booting with that kernel and see it working. I'm guessing you 've nvidia or ATI graphics card you need to install the driver for your card with this kernel. It's problem with nvidia drivers (I don't know about ATI cuz i don't use ATI) that you need to recompile it for every new kernel.

Install the driver again and it'll be fine. I hope you know how to install nvidia driver.

Good luck :)

---

### Post by Saiph on 2009-05-26
I reinstall graphics card everytime was born new kernel. But now, have this problem :(:(
I try reconfgure xserver, uninstall nvidia, but only the black screen after boot , no login screen was apears. 
I thought ubuntu is imperishable.

---

### Post by Saiph on 2009-05-26
**Problem solved**

uninstall 180.51 nvidia drivers, install kubuntu-desktop, get kdm as default, and install proprietary drivers from repositar and it is starting fine

uninstall kde-desktop and all ok. Thankyou zeex.

---

