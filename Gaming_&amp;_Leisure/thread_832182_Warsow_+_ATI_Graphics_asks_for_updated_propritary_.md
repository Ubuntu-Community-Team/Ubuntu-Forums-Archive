---
title: "Warsow + ATI Graphics asks for updated propritary driver"
date: 2008-06-17
forum: Gaming &amp; Leisure
---

### Post by hp_pavilion_39 on 2008-06-17
I'm running Warsow on my Ubuntu 7.10 Gusty machine that has ATI Radeon Express graphics card, and when I start up Warsow, an "xmessage" alert shows up, giving this message:

"XMessage:
You're OpenGL installation doesn't support direct rendering.  If you          have an NVIDIA or an ATI card you'll probably need to install the propritary driver."

What is a propritary driver, and where do I get one, lol  :P

Thanks,
Andrew

---

### Post by acoustibop on 2008-06-17
Go to System -> Adminstration -> Restricted Drivers Manager (AIR; I'm running Hardy now).  You'll need to enter your password.  Tick the box for the ATI accelerated graphics driver; the Restricted Drivers Manager will download the driver and install it.  You'll need to reboot after it's installed.

For optimum results, after rebooting open a terminal and enter```
sudo aticonfig --initial -f

sudo aticonfig --overlay-type=Xv
```and restart X.

---

### Post by hp_pavilion_39 on 2008-06-17
alright, thanks.  System > Administration > Restricted Drivers Manager  ... all the drivers are selected to be running, and I sill recieve the same error when starting Warsow.  

I also tried opening Warsow via terminal, and I recieved this error:

"-laptop:~$ warsow
Xlib: extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)"

What is   LIBGL_DEBUG=verbose   ?

---

### Post by acoustibop on 2008-06-18
Is there an ATI driver included in the drivers in the Restricted Drivers Manager, and if so, how did you install it?

---

### Post by hp_pavilion_39 on 2008-06-22
all the "restricted" drivers are installed, and are in use.  for some reason, I am able to play Cube2 and Sauerbraten, but any OpenGL games don't want to work.  kinda find this weird.  does it mean that maybe my Graphics card isn't powerful enough for OpenGL games?

---

### Post by chewit on 2008-06-23
Seems like you have no 3D support enabled. I would advise you to use the "radeon" drivers which come with Ubuntu. You can find this driver in "Screens & Graphics"

Once you have select "radeon", follow these two tips:

[http://edhewitt.co.uk/2008/03/24/fixing-ati-radeon-on-linux/](http://edhewitt.co.uk/2008/03/24/fixing-ati-radeon-on-linux/)
[http://edhewitt.co.uk/2008/04/07/tweaking-the-ati-radeon-in-linux/](http://edhewitt.co.uk/2008/04/07/tweaking-the-ati-radeon-in-linux/)

---

### Post by hp_pavilion_39 on 2008-06-26
I can use any other games... even ones of higher quality, but only if they do not support OpenGL.  Is there a reason that OpenGL doesn't work on my laptop?

---

