---
title: "Massive screen corruption after 12.10 upgrade"
date: 2012-10-22
forum: Desktop Environments
---

### Post by kevpatts on 2012-10-22
Hey all,

I had 12.04 and I upgraded to quantal 12.10. I initially had problems with VERY slow graphics, but I think that was because I changed the theme and didn't reboot (bug in itself).

I have 2 full HD monitors running off an nVidia 9800 GT card without any problems until now.

I changed to the nvidia drivers to try to resolve this, but they couldn't load at all, so now I'm back on the nouveau drivers.

Everything looks fine normally, but occasionally I get massive corruption within browser windows (popup messages above the window look fine) and sometimes one of my monitors (second one) gets corrupted and I can no longer move the mouse to it; it's as if Ubuntu disables it. The strange thing is that when this happens everything I do causes the corrupt screen to change wildly but nothing happens on my working primary screen. I have to hard reboot when this happens.

Before this happens also, the mouse normally pretty much freezes. It does move, but moves in one big jolt about every 10 seconds, so it's unusable. This was over the auto-hiding dock last time it happened.

Anyone else having the same problems?

Kevpatts

---

### Post by kevpatts on 2012-10-22
Here are example photos.

I'm back running XFCE now and everything is running fine.

---

### Post by MSich on 2012-10-30
> **kevpatts said:**
> Here are example photos.
 
I'm back running XFCE now and everything is running fine.
 
I'm having the exact same issue.  Not the same video card, but, close, also Nvidia.  I was going to try to change the drivers tonight, but now I'm not too hopeful.  Sorry no one has responded with an answer.Mike

---

### Post by linux4me on 2012-10-30
If you look in the [known bugs thread for 12.10]("http://ubuntuforums.org/showthread.php?t=2073060"), you'll see that the linux headers aren't installed in 12.10 by default, and they are not identified as a dependency by the proprietary nvidia drivers in the current version of those drivers, so the install will fail.

You say you did an upgrade, so it's possible that the linux headers would have been carried over and updated from 12.04, but the first thing I would check is to make sure that they are installed in 12.10 by running:
```
sudo apt-get install linux-headers-generic
```

Then if you're sure the nvidia drivers were completely removed, try reinstalling the nvidia current drivers.

---

### Post by kevpatts on 2012-11-05
Thanks for that, but the main problem I'm trying to highlight here is the corruption onf the visuals using the nouveau driver.

In the syslog after this crash I get:
```
Nov  5 14:08:26 kpattison-ubuntu kernel: [ 5111.576929] detected fb_set_par error, error code: -16
Nov  5 14:08:46 kpattison-ubuntu acpid: client 1550[0:0] has disconnected
Nov  5 14:08:48 kpattison-ubuntu kernel: [ 5137.678457] [drm] nouveau 0000:02:00.0: Failed to idle channel 2.
Nov  5 14:08:48 kpattison-ubuntu gnome-session[6241]: Gdk-WARNING: gnome-session: Fatal IO error 11 (Resource temporarily unavailable) on X server :0.#012
Nov  5 14:08:48 kpattison-ub
```

and it just cuts off half way through the logging line.

---

### Post by kevpatts on 2012-11-05
> **MSich said:**
> I'm having the exact same issue.  Not the same video card, but, close, also Nvidia.  I was going to try to change the drivers tonight, but now I'm not too hopeful.  Sorry no one has responded with an answer.Mike

Can I ask what video card you're using? Is it a 9600GT?

---

