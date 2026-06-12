---
title: "Doom 3 Black Screen"
date: 2007-05-14
forum: Gaming &amp; Leisure
---

### Post by BetaMaster on 2007-05-14
When I installed Doom 3 with the linux binaries, it started off working. I configured the graphics so they wouldn't be 800x600 (I have more than enough system specs to do it, so I seriously doubt it's my specs causing the problem), and then I restarted the game. Now, whenever I try launching Doom 3, I just see a black screen. No sound, nothing. Just black, and I have to restart X session to get back to Ubuntu. I have no idea why it's doing this, though I think it might have something to do with the graphical settings being changed (but I don't know *why* it would have done this).
If it *is* the graphics, I don't know how to fix this since i can't get into Doom 3.
Any help?

Thank you!

EDIT
I ran a logfile to see what was going on, this seems to be the only one that seem useful to post:
> ------ OSS Sound Initialization ------
WARNING: failed to open sound device '/dev/dsp': Device or resource busy
WARNING: sound subsystem disabled
It seems to be disabling the sound. That wouldn't explain the black screen though.

---

### Post by BetaMaster on 2007-05-14
Okay so I went in and deleted my configuration files. Then it worked, but it was in 800x600 again. I changed the resolution to 1024x760 and voila! It wouldn't start any more. I don't know why it's doing that though. Does anyone have any suggestions?

---

### Post by lordofchug on 2009-03-08
Hi there, I'm fairly new tu ubuntu myself but I had the same/similar problem after changing the graphics settings from low quality 640/480 to high quality 1024/768.

Here is what I did to fix the problem..

Download doom3_1.3.1.1304-multilanguage.run which is the graphical installer, if you have not already done so from:

[http://liflg.org/?catid=6&gameid=48](http://liflg.org/?catid=6&gameid=48)

run the installer, I installed to /home/myname/doom3

Then I opened System - Administration - Hardware Drivers and was given these options:

NVIDIA accelerated graphics driver (version 173)
NVIDIA accelerated graphics driver (version 96)
NVIDIA accelerated graphics driver (version 177) [Recommended]

The only one that would work was the (version 96) I presume this is the oldest driver as it is the lowest number so maybe if you have the option of an older driver you could try that.

I also set my sound preferences Autodetect

I hope this maybe of help to you.

lordofchug :-)

---

### Post by lordofchug on 2009-03-08
Sorry just noticed how old this post was DOH!

Well anyhow I hope this info helps someone who might have the same issue I had.

:D

---

### Post by RaiCoss on 2009-03-08
Only 500 days late to the party xD

---

