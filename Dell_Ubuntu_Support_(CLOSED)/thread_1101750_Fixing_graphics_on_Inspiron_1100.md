---
title: "Fixing graphics on Inspiron 1100"
date: 2009-03-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by namtrak on 2009-03-20
Gidday,  Firstly Im a long time observer of Linux and first time user - you get the idea.  Anyway, I've decided after much prevarication to install Ubuntu 8.10 onto my Dell Inspiron 1100 - to extend its life just a little longer.

Summary of where I am upto.  Downloaded and installed okay, however the screen resolution in the Monitor Resolution Settings only gives me two options 640 or 800.  Similarly the viewable area is reduced by a large black border (about an inch or so).  I have assumed these two issues are related.

So after much searching I think I have established that.......

1. The synaptics package manager cant find 915resolution, I have added the Universe and Multiverse - I think I read somewhere that 915resolution is now obsolete?

2. I have BIOS A30 with the UMA Video memory set at 8MB.

3. The packages are all updated.

4. Running sudo apt-get install xserver-xorg-video-intel tells me that I already have the latest intel drivers.

5. Running sudo dpkg-reconfigure xserver-xorg takes me through some keyboard setups (after a preemptive thing about video changes) - with or without the Display Manager running

6. I think my xorg.conf is empty.

And that is about where I am upto - suggestions?

---

