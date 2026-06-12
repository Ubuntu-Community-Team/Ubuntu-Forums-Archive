---
title: "Stuck with a resolution in X"
date: 2013-02-12
forum: Desktop Environments
---

### Post by arieunier on 2013-02-12
Hi,
I've switched a few days ago from windows to ubuntu 12.10, and so far i really like it.
I've got a problem though .. I'm doing quite often presentation to clients, using powerpoints or other soft, and i need to share my screen using a projector, a TV, etc ..

I've realized that my resolution is stuck at 1600x900 and i can't change it, either through the nvidia x server, or using the display panel in ubuntu. Thus, image is truncated during my presentations, so i usually only use my laptop.

I've installed the drivers (304.60) for my nvidia card (a quadro FX), on my Lenovo W510.

Can someone help me fixing this ? I'd love being able to select a lower resolution (like 1024x...) during presentation, that would work on most of the projectors or TV.

Many thanks :)

---

### Post by leclerc65 on 2013-02-12
I think I saw similar question a few days ago.
Did you try
   sudo gedit /etc/default/grub
Find line 
   #GRUB_GFXMODE=640x480
Remove #, then change the resolution to the one you want.

---

### Post by arieunier on 2013-02-13
> **leclerc65 said:**
> I think I saw similar question a few days ago.
Did you try
   sudo gedit /etc/default/grub
Find line 
   #GRUB_GFXMODE=640x480
Remove #, then change the resolution to the one you want.

Yes, i've changed it already to something else :

arieunier@OCDCArieunier:~$ cat /etc/default/grub | grep GFX
GRUB_GFXPAYLOAD=1024x768
GRUB_GFXMODE=1024x768

---

### Post by arieunier on 2013-02-14
Any help on this ?
I'm still stuck and can't really do any presentation in front of clients because of this :/

---

