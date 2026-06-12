---
title: "weird desktop after dual monitor fiddling"
date: 2008-05-04
forum: Desktop Environments
---

### Post by one_ro on 2008-05-04
Hi there,

I have a Philips external monitor, for which I have configured the xorg.conf using NVIDIA X Server Settings (of course, I backed-up my initial xorg.conf).

The problem is, everytime I plug-off the external monitor, my KDE desktop's functionality is only a quarter of its normal size, the rest of it being white (see png attached).

I copied the back-up over xorg.xonf, with no avail. Does anyone please have a clue for this, I already spent about three hours playing with the settings in NVIDIA X Server, with every combination possible (TwinView, Clone mode, absolute position) but I just can't get it right.

Now I believe that it's not xorg.conf anymore, but KDE4 itself... I ran out of ideas. If you have a hint, please share it with me.

Thanks in advance,
Adrian

---

### Post by one_ro on 2008-05-04
It's worth mentioning that, for a new user, the behavior dissapears. The desktop is alright for a new user, so it must have something to do with the setting in my home folder, does anybody please have any idea what?

---

### Post by Xiong Chiamiov on 2008-05-04
Not that this is going to be very helpful, but it's going to be hard to get any support with KDE4, since it's so buggy, especially since you think it's a KDE problem.  It's really a good idea to stay with 3.5.9 until 4.1 at least.

That said, try making a copy of your .kde4 folder and let a new one generate (or copy it over from the new user account).  If that solves the problem, then you know it is indeed KDE's fault.  Then just slowly copy over folders until it doesn't work again, and narrow it down bit by bit until you find the file that's causing it.  It'll take a little while, but it's the best way to go about fixing problems like that.  [Trust me.]("http://ubuntuforums.org/showthread.php?t=773550")

---

### Post by one_ro on 2008-05-04
Thanks very much, that's exactly what I've done. Since a new user did not experience the problem, I correctly inferred it was my .kde4 folder causing it. Inside, in the /config folder, there is a file called "plasma-appletsrc" and that was the cause of all evil.

Phew, solved now :D
Cheers,
Adrian

---

