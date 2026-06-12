---
title: "Sync Palm Treo 650"
date: 2009-06-09
forum: General Help
---

### Post by theShaggy on 2009-06-09
I know this has been mentioned time and time again (I have searched) but none of the available solutions seem to apply to anything beyond Gutsy.

I'm running Intrepid 64-bit, which apparently had a sync bug that was fixed in 2008, but I am not able to synch up my Treo 650 to my bluetooth dongle.  It will recognize it, and I can send files to the handset, but I cannot sync, no matter what I do.  It tells me that "the port is in use by another application."

Part of the problem seems to be that I don't have a /dev/pilot, but from my research this isn't a necessary port to have - basically, whenever the Palm syncs to my computer, it should create itself a port to run through.  This appears not to be happening, and I don't know how to make it do so.

I have sudo modprobe visor, loaded Visor, shut down HAL, and used all sorts of known configurations.  Have I missed something vital?  Is this stuff fixed in Jaunty (I'm planning an upgrade later this week)?

Is there any way to see the incoming connections while I try syncing?  I'm at a loss, but have no USB cable and need to get some software and security updates installed.

Thanks!

---

