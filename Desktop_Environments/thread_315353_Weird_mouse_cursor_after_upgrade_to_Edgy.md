---
title: "Weird mouse cursor after upgrade to Edgy"
date: 2006-12-09
forum: Desktop Environments
---

### Post by rklauco on 2006-12-09
I am facing a strange problem.
Right after upgrade, I have a bar under the mouse cursor.
The situation is the same as here:
[http://www.ubuntuforums.org/showthread.php?t=284750](http://www.ubuntuforums.org/showthread.php?t=284750)
I am using fglrx driver.
Not sure which cfg to post...

---

### Post by kEinstein on 2006-12-15
Hi,
have you tried to add the following to your Xorg config?

```
Section "Extensions"
    Option "Composite" "Disable"
EndSection
```

I am experiencing similar problems with my mouse after switching from 'radeon' to 'fglrx' drivers on my primary screen. The problem is even more annoying on my second screen with a 20x20mm square of graphical garbage instead of a mouse cursor. 

To follow this issue, you might want to read the following threads and bug reports, probably we might once find a solution, but there is none (or no acceptable) at the time of writing:
[http://ubuntuforums.org/showthread.php?t=273213&highlight=mouse+cursor]("http://ubuntuforums.org/showthread.php?t=273213&highlight=mouse+cursor")  and
[http://ubuntuforums.org/showthread.php?t=290500&highlight=mouse+cursor]("http://ubuntuforums.org/showthread.php?t=290500&highlight=mouse+cursor") on dual-head systems
[http://ati.cchtml.com/show_bug.cgi?id=544]("http://ati.cchtml.com/show_bug.cgi?id=544") for an official bug report at ATI's support

---

### Post by kEinstein on 2006-12-16
Try [this one]("http://ubuntuforums.org/showthread.php?p=1894588#post1894588")!! Managed to get 'fglrx' working and a clean mouse cursor. Although, the solution applies especially to dual-head issues, give it a try!

---

### Post by rklauco on 2006-12-17
> **kEinstein said:**
> Try [this one]("http://ubuntuforums.org/showthread.php?p=1894588#post1894588")!! Managed to get 'fglrx' working and a clean mouse cursor. Although, the solution applies especially to dual-head issues, give it a try!

Unfortunately, I did.
Now, the mouse is crystalclear.
But, after few times of running screensaver I experience system freeze. Nothing is in logs. This SS uses the OpenGL (some Matrix thingy that my girlfriend likes). For some reason, few times when starting the SS the system freeze.
Everything was working fine with the same WH under dapper, I don't believe this is a HW issue...

---

### Post by kEinstein on 2006-12-18
Hmmm.
I've never spent time on testing the screensavers since I prefer a blank screen when my computer is idle. Having tested 'GLMatrix' and several others, the only thing that I can tell is that they all work great in my case (and do indeed perform great with fglrx) - even after repeatedly activating/disabling them.

In your case, check if your computer suspends to RAM or initiates any other form of power-saving. When I remember correctly from my past experience, there is at least one severe draw-back of using proprietary 'fglrx' drivers compared to 'radeon' or 'ati':  using 'fglrx' with power-saving can freeze the system, disabling them might do the trick! (Don't know if this bug has already been solved in the latest kernel updates)
Also check if your kernel parameters are set to anything with 'vga='. If so - disable the parameter and try running GL screensavers again.

As far as I can tell, everything works fine on my machine. No drawbacks.
Good luck.

---

