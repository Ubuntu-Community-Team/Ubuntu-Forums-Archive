---
title: "Cedega Issue (xFree86 search rather than Xorg)"
date: 2005-10-16
forum: Gaming &amp; Leisure
---

### Post by Mirth on 2005-10-16
I'm trying to run a game with Cedega, and it's fine until the last line, when it quits out:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".

As we all may know, Ubuntu has Xorg instead of Xfree86.  Is there anything I can enter so it looks for Xorg instead?

Are there any other solutions to the problem?

Much thanks.

---

### Post by claydoh on 2005-10-16
What video card do you have, and do you have 3d acceleration enabled? Are there any other errors as well?

The reference to Xfree probably due to Xorg being based on it.

---

### Post by Mirth on 2005-10-16
I have an ATI Radeon 9600.

There are no other errors, and I don't know how to enable 3D Acceleration.

---

### Post by seethru on 2005-10-16
you'd have to install your videocard drivers, since it's ati you'll be looking for the fglrx drivers in synaptic. Once you've grabbed those you'll have to modify your xorg.conf to read fglrx instead of ati, and then restart X.

---

### Post by claydoh on 2005-10-16
[try here for a How-to,]("http://ubuntuforums.org/showthread.php?p=408111") there are other posts as well. I don't have any ati hardware so I have no experience setting one up, but the How-to should get you going :)

---

### Post by TLE on 2005-10-16
Well, you'll need to install the ATI drivers to get 3D hardware acceleration, DON'T install the ones from their website, it won't work. Look for my post in this thread [http://www.ubuntuforums.org/showthread.php?t=76846&highlight=slow]("http://www.ubuntuforums.org/showthread.php?t=76846&highlight=slow")
to get some how to's on how to install the drivers. When you have done that, or if you already have, you can check if you have 3D hardware acceleration with:
```
fglrxinfo
```
If it says MESA anywhere in the output the 3D hardware acceleration from your ATI card is not being used. Good luck.

---

### Post by Mirth on 2005-10-16
I installed my drivers via Synaptic.

I'll go over your guys's stuff though.

---

