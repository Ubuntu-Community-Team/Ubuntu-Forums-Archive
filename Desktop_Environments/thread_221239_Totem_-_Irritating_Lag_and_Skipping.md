---
title: "Totem - Irritating Lag and Skipping"
date: 2006-07-22
forum: Desktop Environments
---

### Post by asplode on 2006-07-22
I have the latest version of totem compiled and installed on my Dapper installation...  But lately I've been having a problem...

All my video looks choppy, and DVDs refuse to play, even though I have the dvdread3 & libdvdcss2 packages.

All my videos run fine in gxine, but I cannot figure out how to change my default players.

I've tried switching totem between totem-gstreamer and totem-xine, I've recompiled it several times, with each package in place, and nothing seems to help...

I'm about to pull my hair out.

---

### Post by Ben Armston on 2006-07-22
To change the default player start System -> Preferences -> Removable Drives and Media, go to the multimedia tab and change "totem %m" to "gxine %m".

Ben.

---

### Post by asplode on 2006-07-22
> **Ben Armston said:**
> To change the default player start System -> Preferences -> Removable Drives and Media, go to the multimedia tab and change "totem %m" to "gxine %m".

Ben.

thanks for the tip...

any idea why totem is stuttering or unable to play DVDs?

I like totem to an extent, and wouldn't really mind using it as my default player, but I'm just not sure whats going on...

I doubt enabling fastwrites on my NVIDIA AGP card had anything to do with it...

---

### Post by ardchoille on 2006-07-22
Also, you might want to enable dma on the device: [https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

That will make the movie smoother.

---

### Post by asplode on 2006-07-22
> **ardchoille said:**
> Also, you might want to enable dma on the device: [https://wiki.ubuntu.com/DMA](https://wiki.ubuntu.com/DMA)

That will make the movie smoother.

I appreciate it, however, the problem is not only with DVDs but any video file on my HDD.  The DVD error is a pop up window that tells me that totem cannot find a suitable plugin to decode the DVDs with...

I'm using Totem 1.5.4... should I downgrade to the version in the repos?  I was having internal data flow errors with the repo version, so I decided to try and compile the newest available.

Also, DMA is already enabled.

---

### Post by Ben Armston on 2006-07-22
I don't know why Totem wouldn't be working correctly. It doesn't work too well at DVD playback for me, but I have a very old machine, P3 with only 384M of RAM. :( 

If gxine is fine and totem-xine is not, it does sound like a problem with totem rather than the underlying xine library.

Sorry I can't offer any more help.

Ben.

---

### Post by asplode on 2006-07-22
After downgrading to totem-1.4.1, and switching over to totem-gstreamer, the same problems persist.  I'm going to keep messing with it and see if I can come up with any solutions in the meantime, if I do, I'll post back.

---

### Post by asplode on 2006-07-22
Thanks for your help everyone, especially the tip on how to switch media players.

I've resolved my problem, although I'm not exactly sure what did it.

I reinstalled everything gstreamer related, installed mplayer (haven't opened it yet though) and switched the totem back to totem-xine.

The stuttering is gone and DVD playback is all up in the house again!

---

