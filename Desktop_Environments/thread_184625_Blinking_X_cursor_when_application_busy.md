---
title: "Blinking X cursor when application busy"
date: 2006-05-30
forum: Desktop Environments
---

### Post by alex_still on 2006-05-30
Hi all,

I've searched the forum but haven't seen this issue raised before, apologies if I'm wrong.  I've recently switched from breezy to dapper, without any problem, but for one small thing : When an application is busy (ex. firefox loading a page) the cursor turns into an animated  "clock". This worked fine in breezy, but in dapper the animation makes the whole cursor blink heavily. I have the issue regardless of the X server (Xorg, Xgl) and driver (nv or nvidia).

If that's relevant,  the graphic card is a 6600GT. I'd be happy to hear from others experience or on how to diagnose the problem more precisly.

(Yes I know, this is a minor issue !)

Cheers,

-- 
Alex

---

### Post by GoA on 2006-05-30
This is a known bug.

---

### Post by medgno on 2006-05-30
Yeah, I got this problem too. What I did was I edited the 'Human' mouse cursor theme to get rid of all the animations and it seems to work. To install it, extract the .tar.gz to ~/.icons/  and then go to System->Preferences->Mouse preferences, and select the 'HumanMod' cursor theme. Hope this helps!

---

### Post by alex_still on 2006-05-31
Thanks for the tip !

---

### Post by Shakabab on 2006-06-02
[QUOTE=alex_still]Thanks for the tip ![/QUOTE]

I agree with, very usefull information. The same bug occured and thanks to you I quickly found means to solve it. Thanks for the effort medgno!

In case any one else is slightly confused by medgno's instructions on installing, you can find the .icons mentioned in your home directory. You might have to turn on 'view hidden files' using the view button on top of your window or press ctrl + h on the pc. Which would probable be command + h on the mac but I'm not sure about that.

Absolute path would be something like /home/**username**/.icons/

---

### Post by BitTorrentBuddha on 2006-06-07
I have the same problem, but only since I got my video card (geforce 6200), any clues as to how to fix it without getting rid of the animations?

---

### Post by atenlaugh on 2006-07-12
I thought there was some sort of fix involving your xorg.conf (I had it working before, but due to issues, my xorg.conf is now different). I can't figure out what I did... 

Anyway, IT'S an option for keeping animations, and is very simple, if anybody can provide exactly what to do.

---

### Post by sandpaperback on 2006-07-12
In your /etc/X11/xorg.conf file put this line into the Nvidia device section:

```
Option     "SWCursor"     "True"
```

If there's a "HWCursor" line there, set it to False.  It's just that easy and you can keep the animation. :)

---

