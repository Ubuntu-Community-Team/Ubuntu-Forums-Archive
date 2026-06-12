---
title: "KMix volume control intervals"
date: 2009-02-13
forum: General Help
---

### Post by lotharamious on 2009-02-13
Regarding T**Kmix**

Kubuntu 8.10 w/KDE4.2
Xonar DX
2.6.27-11-generic x86-64

First, no problems with controlling volume.  Hotkeys function properly.  My question is how to change the volume step/interval of Kmix.

For example, a single press of the 'Volume Up' hotkey yields a 5% increase in volume, and a corresponding inverse change when I press the 'Volume Down' hotkey.  Is there any way to change this to say 1% change?

Also, (this may or may not be related), I have this issue where when I set the master volume at 50% or below, the volume seems to completely turn off, but is very loud at 100%(like it should be).

When I run alsamixer the audible range seems to be between -0dB (100% on the slider), and -64dB (50% on the slider).  The scale for me goes down to -128dB (0% on the slider).

Any ideas for either of the above problems?  The first problem is more annoying than the second, although I suppose fixing the second one first would also remedy the first one.

Thanks guys.

---

### Post by lantor on 2009-05-05
Hi!

Im afraid that i dont have any solutions for you. 

I just wanted to say that I, too, am annoyed by the first problem you described. 
Have you, (or anyone), found a way to change the volume steps in Kubuntu?
Its fairly easy in Ubuntu but the config-editor is only for gnome.

Im running Kubuntu 9.04 on Dell XPS m1330.

---

### Post by Zorael on 2009-05-06
That sounds like a driver quirk. See [http://ubuntuforums.org/showthread.php?p=5017453#post5017453](http://ubuntuforums.org/showthread.php?p=5017453#post5017453) for some general information.

As for changing kmix volume "steps", that likely requires tweaking the source a bit and recompiling it. Sounds like something you could post a KDE bugtracker wishlist report for, though.

---

