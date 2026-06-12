---
title: "Xubuntu keeps changing resolution at random"
date: 2019-03-04
forum: Desktop Environments
---

### Post by grutten on 2019-03-04
Hi everyone,

I'm fairly new using Linux. 
And i ran into a problem i can't seem to fix myself by googling it...

I'm using an Intel Nuc(nuc6cayh) on my Samsung TV (UE50HU6900S).
Running Xubuntu 18.04.2

The problem is that the Xubuntu keeps changing resolution.
I want to keep the standard 1920x1080 Full hd resolution.
But the box keeps changing to 3840x2160 at random.
Sometimes it boots in 1080p. Sometimes in 2160.
Also after going to "blank" from management the resolution changes.
I also disabled the power management but now i still have the problem at boot.

To fix the screentearing problem i already created the xorg config file. 
Is there maybe a line i can add there to fix this problem? 

Kind regards,

Glenn

---

### Post by CatKiller on 2019-03-04
> **grutten said:**
> I want to keep the standard 1920x1080 Full hd resolution.
But the box keeps changing to 3840x2160 at random.
As far as I can tell, 3840×2160 is the native resolution of that TV. You will get the best picture quality by setting the resolution to that, and using scaling if you need to make things display larger. 

It is likely that the mechanism whereby your display advertises its resolution capabilities is affected by which is turned on first. Some experimentation might help you find a pattern. You might also consider setting up some kind of shortcut to quickly switch between the resolutions for those times that it has defaulted to the wrong one. 

> To fix the screentearing problem i already created the xorg config file. 
Is there maybe a line i can add there to fix this problem? 

It's a while since I played with it, but I think that specifying a mode in the Monitor section will allow you to prefer only that mode.

I suspect that you can also specify a mode other than Auto in the screen resolution tools to have a similar effect, although I've not used Xfce for quite a long time.

---

### Post by grutten on 2019-03-08
Hi Catkiller,

Thanks for the reply.
Unfortunately i have no way of changing native resolution on the TV itself.
It looks like i'm having the same problem with the audio to.
It should keep on HDMI output but it always changes to analog output...

In the "display gui" in xfce i set the resolution to 1920x1080 there is no auto function.

---

### Post by CatKiller on 2019-03-08
> **grutten said:**
> Unfortunately i have no way of changing native resolution on the TV itself.

The native resolution of a display is a physical characteristic. You would change it by taking a chainsaw to it and slicing off chunks of smaller size.

Running it at a lower resolution simply means that you're using 4 pixels on the screen to display one pixel's worth of the image.

>  It looks like i'm having the same problem with the audio to.

That sounds like a cabling issue, or your TV not being on when the computer is turned on so that it can't auto-detect.

---

### Post by Autodave on 2019-03-08
+1 with CatKiller.  Have the TV on first and then power the PC.  You may also want to try another cable.  Realize that any cable can fail.  Also, realize that some earlier and/or cheaper HDMI cables can't handle what you are asking it to.

---

