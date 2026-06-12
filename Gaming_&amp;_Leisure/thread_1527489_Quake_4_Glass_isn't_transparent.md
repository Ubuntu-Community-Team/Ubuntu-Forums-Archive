---
title: "Quake 4 Glass isn't transparent???"
date: 2010-07-09
forum: Gaming &amp; Leisure
---

### Post by Durandal512 on 2010-07-09
Yesterday I got the Quake 4 Special DVD Edition box set.  It installed perfectly, runs great, and I fixed the sound problem I had at first.  Only problem is that large windows (such as those in the control room of the Nexus Hub) are black, when I know they are supposed to be transparent.  I've attached screenshots.  I will do my best to describe the issue with each of the images.

Screenshot-Quake4.png:  This is one of the windows in the Nexus Hub.  Where you see a blue-greyish slab is supposed to be a transparent window.

Screenshot-Quake4-1.png:  This is from the beginning of the game.  They look like two metal slabs with the Strogg insignia, but they are supposed to be transparent windows.

Screenshot-Quake4-2.png:  Also from the beginning of the game.  Shows the smaller windows above the Strogg-insignia ones.  Like the above, also should be transparent.

It may also be useful to note that smaller windows (or maybe just other windows, I'm not entirely sure) work fine and are transparent as they should be.

I have never had this problem with any other games.  I run Doom 3, the Unreal Tournament 2004 demo, Nexuiz, and the Penumbra trilogy all with no transparency problems.

I am running Quake 4 on Ultra-Quality (have tried lower, didn't fix the problem) at 1024x768 on a Dell Inspiron 530S with an NVidia GT 220 with the latest drivers on Ubuntu 10.04.

Can anyone help me?

---

### Post by realzippy on 2010-07-09
Have you tried to modify the config file?

Have a look here:

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=512940](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=512940)

---

### Post by Durandal512 on 2010-07-09
Thank you.  I had tried searching for "Quake 4", but apparently "4" is too short a term and considered unimportant.

I looked into the Quake 4 config file and saw that I (like the original poster in the link you provided) did not have an entry for "alphaToConverge".  So, I put in one, and set it to 0.  This did not work.  It turns out that it is supposed to be "alphaToCoverage", an entry which I already had.  I set it to 0, and it worked.  Now I can play Quake 4 the way it is meant to be played. I should probably post a correction on that thread, though.

---

### Post by realzippy on 2010-07-09
> **Durandal512 said:**
> Thank you.  I had tried searching for "Quake 4", but apparently "4" is too short a term and considered unimportant.

I looked into the Quake 4 config file and saw that I (like the original poster in the link you provided) did not have an entry for "alphaToConverge".  So, I put in one, and set it to 0.  This did not work.  It turns out that it is supposed to be "alphaToCoverage", an entry which I already had.  I set it to 0, and it worked.  Now I can play Quake 4 the way it is meant to be played. I should probably post a correction on that thread, though.

Yes,that would be useful.
Please also set this thread as "solved"....happy fraggin'!

---

