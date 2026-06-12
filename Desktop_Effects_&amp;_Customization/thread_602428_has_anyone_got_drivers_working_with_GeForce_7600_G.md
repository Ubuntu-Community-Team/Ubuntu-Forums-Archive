---
title: "has anyone got drivers working with GeForce 7600 GS?"
date: 2007-11-04
forum: Desktop Effects &amp; Customization
---

### Post by Arizon_Dread on 2007-11-04
as the title says.

I can't get it working!
I tried with 
1. Envy
2. Modifying my xorg.conf to use Nvidia-drivers and other stuff.
3. Reinstalling Gutsy (I originally updated from feisty)
4. Restricted Drivers Manager
5. Reinstalling xorg.


Everything returns low graphic mode on reboot.
I'm out of ideas.. Does anyone know if there are some special drives for this model of graphics card?

Could it be because of my screen? it's a ViewSonic E70f+
does this matter?

My primary objective is to get compiz fusion to work. I really LOVE the cube and I have to get it working, I feel disabled without it. :)

please! help me!

---

### Post by tseliot on 2007-11-04
The "low graphic mode" you mentioned might be the effect of the "Bullet-proof X" which sets the driver to "vesa" when the Xserver fails to start. There must be a reason for this failure.

You might ask here (Nvidia's staff should be able to help you):
[http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14](http://www.nvnews.net/vbulletin/forumdisplay.php?s=&forumid=14)

---

### Post by henjenagin on 2007-11-04
Not sure if it matters, but I have it working with GeForce 7600 GT.

---

### Post by thepineApple on 2007-11-04
Try this:

1. install the 100.14.19 nVidia driver (if you have already, reinstall it. just to make sure)

2. after reboot, don't worry about the low resolution, go to a terminal (Ctrl+F1), log in, then dpkg-reconfigure xserver-xorg, this will guide you to reconfigure xorg. From memory, in the second menu where you need to choose your driver, there should be a 'nvidia' option in the list, which is the newly installed driver. MAKE SURE YOU CHOOSE THAT.

3. finish the rest of the process with your own preference, then reboot

4. this time it should be able to go in to the correct resolution after the reboot.

hope this works for you.

   **- the PA**

---

### Post by Arizon_Dread on 2007-11-05
Thanx for your replies, but I got it working yesterday after a lot of help.

The problem consisted of two different things.

1. The NVIDIA driver wouldn't install correctly. I installed the necessary packages for compiling the kernel interface that I got prompted about during installation of the driver. I also needed to be root in order to compile the kernel interface ("sudo su -").

2. There was an extra power-plug that needed to be connected to the graphics card. I had never even heard of this before, so I had no idea about this.

once these things were fixed, it worked.

---

### Post by thkatsou on 2008-06-07
Had the same problems. I found from your last post that the card had a power connector!!
By the way that was said  on the card manual too. 
After plugging the power the problem solved after 1-2 tries and surely a 
dpkg-reconfigure xserver-xorg.

---

### Post by BatKoos on 2008-06-13
Guys, great to hear you managed with your NVidia GeForce 7600 cards...
However...would someone mind putting together a step by step guide how to get the results that you're talking of...for a noob like myself...
That would be awesome...!
L8r!

---

