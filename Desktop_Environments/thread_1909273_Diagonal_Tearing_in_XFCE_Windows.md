---
title: "Diagonal Tearing in XFCE Windows"
date: 2012-01-14
forum: Desktop Environments
---

### Post by Maximus559 on 2012-01-14
I recently upgraded to Xubuntu 11.10, and so far, everything is working *almost* perfectly. The only problem I've run into is a slight graphical glitch which manifests itself when windows are opened, minimized, maximized, or scrolled quickly. It's not a huge problem, but it is starting to get on my nerves.

The glitch can best be described as a kind of diagonal tearing. To illustrate the effect, I've attached an image I made using Gimp which roughly approximates what I am seeing (couldn't think of a way to capture the real thing). Again, this glitch is visible for a split second whenever a window is rapidly refreshed; moving a window, however, does not produce this effect.

Turning off compositing seems to eliminate the tearing, but I don't consider this to be an acceptable solution. Any ideas as to how I might go about fixing this problem?

System specs:

Dell Dimension 4500
Pentium 4 1.8A GHz
1 GB RAM
Geforce4 MX 420 (AGP 4x, uses proprietary nvidia-96 drivers)

---

### Post by typhoon_tip on 2012-01-15
Try this first:

Open CompizConfig Settings Manager, go to General, OpenGL and untick "Sync to VBlank", tell me if the problem is still there (logoff and login again may be a good thing to do). After you untick, give it a few seconds to "recompose" itself...

If not working, I have other ideas.

---

### Post by cottfcfan on 2012-01-15
Xunbuntu doesn't use compiz.
It's probably a graphics card issue, can't be of anymore help though, as I have an integrated intel graphics card.

---

### Post by Maximus559 on 2012-01-15
> **cottfcfan said:**
> Xunbuntu doesn't use compiz.

Correct. I do have an option for "Sync to VBlank" under the OpenGL section of my Nvidia X Server Settings, but it's already unticked.

> **cottfcfan said:**
> It's probably a graphics card issue

Seems that way. I suspect it may have something to do with the new nvidia-96 drivers, which were updated recently to support versions of XOrg later than 1.7.6. I say this because I didn't see any tearing when I was running Ubuntu 10.04, which used the older version of these drivers. Then again, so many other variables have changed that it's hard to tell.

---

### Post by cybergalvez on 2012-01-15
have you tried any of the other nvidia drivers?

---

### Post by Maximus559 on 2012-01-15
Actually, I was just looking into that. When I boot from the live CD, the nouveau drivers are used by default, and the tearing problem does not seem to be present. However, I can't seem to get my hard drive install to stop using the proprietary nvidia-96 drivers. If I click "Remove" in the Additional Drivers menu, nothing happens (i.e, it claims to have uninstalled the nvidia-96 drivers, but they still load themselves on subsequent reboots).

So, this might be a viable solution, if I find a way to disable the proprietary drivers. Is there any downside to using the open source nouveau drivers? I've never had a reason to try them before.

---

### Post by Maximus559 on 2012-01-15
Ah, just figured it out. I had to go into the Software Center and uninstall another nvidia-96 package that the Additional Drivers menu had failed to remove. I'm now using the nouveau drivers, and the diagonal tearing problem appears to have gone away. So far, so good.

If the nouveau drivers don't create any new problems, I'll mark this thread as solved. Again, is there any foreseeable downside to using the nouveau drivers rather than the proprietary ones from Nvidia? I don't plan on running many 3D applications on this machine, so 3D performance isn't too big of an issue. I do need my system to be rock solid stable, though.

---

