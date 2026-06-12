---
title: "How to disable ALL desktop effects"
date: 2011-12-14
forum: Desktop Environments
---

### Post by d0.higgs on 2011-12-14
Hi all,

This issue is killing me, really. I want to stop all desktop effects... for that I was using gnome (no effect) but a friend of mine asked me to try a cairo-dock which enabled some effects (open-gl) on my desktop. Now I have removed the cairo-dock but I am still left with some effects that is causing moving files on my desktop make a trail behind them...

Ubuntu 11.10 is the worst thing ever happened in Ubuntu. :sad:

---

### Post by pastalavista on 2011-12-14
At the log in screen, click the 'gear' icon and you should see the option to boot 'Ubuntu 2D' which, as I understand, has no graphics effects for lower powered graphics processors.

---

### Post by Frogs Hair on 2011-12-14
This post may be of interest . [http://ubuntuforums.org/showthread.php?t=1886799](http://ubuntuforums.org/showthread.php?t=1886799)

---

### Post by d0.higgs on 2011-12-14
Thanks for the replies.

I really tried these, among other methods, before I post. I seem not to be able to remove these desktop effects.
They are very difficult to live with. I installed IceWM as another WM for now. but I am also preparing a new machine for another distro installation (yes, to that extent I am willing to get rid of this/these effects)

I hope someone can tell us how to sovle this issue - how to get rid of ALL desktop effects shipped with Ubuntu 11.10. It's amazing how they made almost impossible to find the settings anywhere in the available menues!

---

### Post by jimmydean886-2 on 2011-12-14
IceWM is very minimal. If you want to keep Unity, just switch to XFCE and add unity-2d-spread to your startup apps.

---

### Post by jimmydean886-2 on 2011-12-14
Out of curiosity, do you have any additional drivers installed?

---

### Post by d0.higgs on 2011-12-14
@jimmydean886-2

nvidia - but ihave it since ages and had not such a stupid problem before.

---

### Post by d0.higgs on 2011-12-15
Solved!
I installed cairo-dock again, with composite-manager-toggle, and I clicked toggle. It asked for confirmation, I said yes. all is fine.
I don't know what exactly happened, but all is fine now - at least almost fine now.
Let someone ask them to get things as good and as clear as Ubuntu11.04.

I will remove cairo-dock stuff and see what will happen.

---

### Post by Krytarik on 2011-12-15
> **d0.higgs said:**
> I installed cairo-dock again, with composite-manager-toggle, and I clicked toggle.
Then it's maybe this?:
```
gconftool-2 --toggle /apps/metacity/general/compositing_manager
```
If yes, this has always been a hidden setting, unless any third-party app makes it accessible. ;-)

Regards.

---

