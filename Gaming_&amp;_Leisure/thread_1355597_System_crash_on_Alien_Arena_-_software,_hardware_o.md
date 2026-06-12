---
title: "System crash on Alien Arena - software, hardware or driver?"
date: 2009-12-15
forum: Gaming &amp; Leisure
---

### Post by overfiend1701 on 2009-12-15
I was playing Alien Arena for the first time this morning. Just a quick play around, mostly to test my systam would run it, before I went to work

But just as I was falling quite rapidly as an alien was firing a particularly graphically impressive gun at me, Kubuntu froze.

This was a new experience for me. I've never had a Linux-based OS crash on me before. Ever!

Which is why I was wondering if it was my graphics card not being up to the task and tripping over. Or the open source drivers not being able to handle interpreting the graphics (because the open source drivers only have partial 3d support for the 9600 pro)

I know I should really wait until I get home to try it again and see if it falls over again. But its worrying me slightly so I thought I'd put it to the forum :)

---

### Post by joeelmex on 2009-12-15
I would not use the open source drivers and go and download the NVIDIA drivers from the Nvidia web site.  They are a easy to install and bring up your gaming needs to a higher level.

---

### Post by Melcar on 2009-12-15
Play the game at low settings.  Some effects cause problems with the open source drivers.  I've been playing the game on my HD4850 and even with the experimental 3D the game works rather well (slow, but playable).

---

### Post by Love2MeetU on 2009-12-15
Sounds like the graphics card is either not upto it, or the driver isn't. Either way, you may need to turn down the game settings; experiment a bit. My son's PC (which is made from old spare parts) has a 64mb AGP card, and was crashing with Alien Arena 7.33, but after the game's settings were turned down lower it all worked out fine. The basic settings for Alien Arena are set at "medium", which is still too high for older or less powerful machines.

---

### Post by Irritant on 2009-12-15
Sounds like the driver probably doesn't have good GLSL support.  Definitely try drivers from Nvidia's site.

---

### Post by tommcd on 2009-12-16
You can get the nvidia driver from the K/Ubuntu repositories. Just install it via apt-get or synaptic. Or go to: system > administration > hardware_drivers to enable the driver. (NOTE: For Kubuntu, I think the path is: KMenu > System > Hardware Drivers Manager). 
You should try the nvidia driver from the Ubuntu repos before using the driver from nvidia.com. This way Ubuntu's APT package manager will keep track of driver updates, and reinstalling the driver whenever there is a kernel update.

If you still have problems after enabling the nvidia driver, then turn off compiz or any desktop effects if you have them enabled.

---

### Post by Melcar on 2009-12-16
Did nvidia ever come out with a 9600 **_PRO_** :lolflag:?  And they don't have open source drivers that provide 3D either; that's only Intel and ATI.

---

### Post by Irritant on 2009-12-16
> **Melcar said:**
> Did nvidia ever come out with a 9600 **_PRO_** :lolflag:?

LOL, you're right, that's an old ATI card.

---

### Post by joeelmex on 2009-12-17
Yikes my mistake, I was thinking of the 9600 GT, didn't realize people still used the old radeon 9600 Pro cards.

---

### Post by Irritant on 2009-12-17
On that note, I should have mentioned, go into the video options, and click on "low" or "lowest" and it should run fine.

---

### Post by overfiend1701 on 2010-02-07
> **joeelmex said:**
> Yikes my mistake, I was thinking of the 9600 GT, didn't realize people still used the old radeon 9600 Pro cards.

Of course I'd use a 9600 pro. Its one of the only decent 3D cards I could get for £15 :D 

Price over performance, that's what I always say ;)

Many thanks for your help. You were all right. Seems as soon as I turn down settings on games to low quality, everything is grand.

Thanks people

---

