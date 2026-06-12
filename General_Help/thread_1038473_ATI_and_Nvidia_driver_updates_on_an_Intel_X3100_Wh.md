---
title: "ATI and Nvidia driver updates on an Intel X3100? What's going on???"
date: 2009-01-12
forum: General Help
---

### Post by kanati on 2009-01-12
Hi,

   I was going through the update manager and I noticed that three updates pertaining to Nvidia and ATI video drivers are awaiting install (nvidia-177-modaliases, xserver-xorg-video-ati, xserver-xorg-video-radeon).  The thing is, I've got a Dell 1420 running off an integrated Intel X3100 graphics chip.  Why is the update manager trying to update ATI and Nvidia drivers when (presumably) there are no such drivers installed on this system?  Are these updates safe to install, or am I going to be staring at a command line after reboot?

Thanks!

-Ubuntu 8.10
-Dell 1420
-Intel 965 Chipset - X3100 GPU
-Core 2 T5450
-Intel wifi card

---

### Post by J03y on 2009-01-12
> **kanati said:**
> Hi,

   I was going through the update manager and I noticed that three updates pertaining to Nvidia and ATI video drivers are awaiting install (nvidia-177-modaliases, xserver-xorg-video-ati, xserver-xorg-video-radeon).  The thing is, I've got a Dell 1420 running off an integrated Intel X3100 graphics chip.  Why is the update manager trying to update ATI and Nvidia drivers when (presumably) there are no such drivers installed on this system?  Are these updates safe to install, or am I going to be staring at a command line after reboot?

Thanks!

-Ubuntu 8.10
-Dell 1420
-Intel 965 Chipset - X3100 GPU
-Core 2 T5450
-Intel wifi cardI don't think so. I'm a newbie with the subject about drivers and graphics cards but every time I re-install Ubuntu I always enable ALL the updates and install them and then when I reboot everything goes fine w/o problems.

---

### Post by jerome1232 on 2009-01-12
> **kanati said:**
> Hi,

   I was going through the update manager and I noticed that three updates pertaining to Nvidia and ATI video drivers are awaiting install (nvidia-177-modaliases, xserver-xorg-video-ati, xserver-xorg-video-radeon).  The thing is, I've got a Dell 1420 running off an integrated Intel X3100 graphics chip.  Why is the update manager trying to update ATI and Nvidia drivers when (presumably) there are no such drivers installed on this system?  Are these updates safe to install, or am I going to be staring at a command line after reboot?

Thanks!

-Ubuntu 8.10
-Dell 1420
-Intel 965 Chipset - X3100 GPU
-Core 2 T5450
-Intel wifi card

I Have an nvidia card and I got those update's dealing with ati cards as well, didn't cause any problems. Perhaps they are just ways for xorg to configure itself for certain problem cards from nvidia/ati should you ever plug one in.

---

### Post by kanati on 2009-01-12
I was thinking the same, but just wanted to be sure.  If the worst happens (ie. unbootable OS), can I use to the live disk to recover my data to an external hard drive?

---

### Post by Arup on 2009-01-12
I get those upgrades as well, I guess thats the part of the plug and play component of Ubuntu, it keeps drivers of all cards in system should one decide to change cards, that way one won't need to go blank every time a new card is put in the system.

---

