---
title: "MythTV hangs on channel change: PVR-350 SBLive"
date: 2006-05-26
forum: Desktop Environments
---

### Post by riptram on 2006-05-26
Sound and video work on the first channel when the application starts. If I try to change the channel, mythfrontend hangs and I get the following in the terminal:

taking too long to be allowed to read..
taking too long to be allowed to read..
Waited 4 seconds for data to become available, waiting again...

I read that this might be a problem with my soundcard or soundcard drivers. I'm using Breezy with SBLive (ALSA). As far as I can tell, this problem was supposed to go away with the newer ALSA versions. Could it be related to the none of my Default sound Sources testing correctly? I "failed to construct test pipeline" for OSS, ALSA and ESD sources.

I'm running the 2.6.12-10-686 kernel and I'm using an A7M266 mobo.

I've already reinstalled everything from scratch once to make sure I didn't screw up myth's setup... I'd appreciate _any_ help you can give!

---

### Post by riptram on 2006-05-27
I'm still thinking this has something to do with sound. Myth frontend outputs:

Disable DPMS
Opening audio device '/dev/dsp'
Opening OSS audio device '/dev/dsp'

So, I'm not using ALSA? How can I change this?

---

### Post by riptram on 2006-05-27
I changed the output device in myth from "/dev/dsp" to "ALSA: default"

This didn't work but has helped me out a little... MythTV warned me that it was starting up without audio. I still can't change channels without the above problems; so, I suppose the problem is not with my sound drivers?

If I force quit mythfrontend then run it again, it can't seem to connect to mythbackend. How can I look at mythbackend messages?

---

