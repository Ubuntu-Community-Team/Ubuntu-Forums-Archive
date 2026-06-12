---
title: "Unichrome, openchrome, savage? Correct via graphics driver?"
date: 2009-04-13
forum: General Help
---

### Post by Bucky Ball on 2009-04-13
Hi all,

Our admin computer at home is an old AMD socket A processor, 1Gb RAM, MB V4MDM with VIA KM400 chipset. From lspci:

```
01:00.0 VGA compatible controller: VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)
```

The manual for the board tells us:

> Integrated VGA: UniChrome graphic acceleration

Everything works fine; great for what it does with Xubuntu install and ubuntu-desktop loaded into that. Except for watching things online. What we want to watch is here:
[HTML]
http://www.abc.net.au/iview/[/HTML]

Loads fast and we have plenty of speed for data transfer, but vid is jittery. Picture quality is superb, but stutters. On further investigation, realise I should probably have the xserver-xorg-video-unichrome driver installed for this machine. I have been using openchrome.

When I click the box to install unichrome, tells me it needs to uninstall a heap of other packages, and some pretty major ones at that, ubuntu-desktop among them! There are things online regarding this and installing the Unichrome driver seems to be the next step, but uninstalling everything else to do it seems a little severe.

So I tried the xserver-xorg-video-via driver but that will not give me 1366x768 resolution, which is correct and offered by the openchrome driver. And vid still stutters.

So, how can I get around this? Works okay on Windoze on the same box. Are there other things I can try to fix the stuttering vid? Is it the 1Gb of ram? Works fine on the other two machines, but they both have 2Gb.

Any suggestions appreciated, and if you have this chipset and working graphics, even better!

---

### Post by Bucky Ball on 2009-04-14
I ran 'compiz-check' to see if that might throw any light. From the output I'm guessing that the openchrome driver is the wrong one. So, how do I go about changing that to the unichrome one without uninstalling all the other packages I wonder?

This is the output of compiz-check:

```
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         VIA Technologies, Inc. VT8378 [S3 UniChrome] Integrated Video (rev 01)
 Driver in use:         openchrome
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: openchrome driver in use 
```

One thing I should add is that the screensaver is totally screwed also. When I open up the gui the screen starts getting strange, let alone when the screensaver kicks in. The whole thing goes on an angle, if that makes sense.

---

### Post by Bucky Ball on 2009-04-18
A rare bumpity bump for this one. I'd really like to solve this problem without destroying my configuration in the process! (Plus, I haven't got time to screw about fixing it at the moment. :))

What I really would **like some info** on, essentially, is what can I do about the fact that **installing** the **unichrome** driver via Synaptics **un-installs ubuntu-desktop** and a heap of other things (a lot). After I **install** the** unichrome** **driver**, is there a **way of re-installing** **what's** been **removed**? Via apt-get as the desktop will be removed (then again, I have got xfce on this machine also)?

Anyone?

---

