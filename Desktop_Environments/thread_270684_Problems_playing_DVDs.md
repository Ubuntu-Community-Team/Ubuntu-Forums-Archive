---
title: "Problems playing DVDs"
date: 2006-10-03
forum: Desktop Environments
---

### Post by KingFuzz on 2006-10-03
I've tried to ask this question over in the beginner's forum, my problem hasn't been solved yet.

[link to thread]("http://www.ubuntuforums.org/showthread.php?t=270555")

I'm unanble to play dvd's in totem. All codecs have been installed, so that's not the problem. Someone suggested I should try ogle, and this program can play dvd's, though with error-messages.

!No accelerated IMDCT transform found
SNDCTL_DSP_GETCHANNELMASK: Invalid argument
+No accelerated colorspace coversion found


My question is, how can I enable playback in Totem?

Thanks in advance..

(EDIT: forgot to type in the error-messages)

---

### Post by ahaslam on 2006-10-03
You need to remove totem-gstreamer and install totem-xine ;)

Tony.

---

### Post by KingFuzz on 2006-10-03
Thank you for the advice, but totem-xine is already installed. Totem-gstreamer isn't installed, but other gstreamer packages are. I'll try to remove those..

---

### Post by ahaslam on 2006-10-03
Out of curiosity, does Mplayer work? If Mplayer can't play it, you've probably got some missing libs ;)

Tony.

---

### Post by KingFuzz on 2006-10-03
M-player gives the following error:

Error opening the selected video out device.

So this might be related to my graphics card? But then i shouldn't be able to play the dvd i ogle.. Hmmm, I'm puzzled..

EDIT:
I found a video out option and changed it to gl. Now the DVD starts, but hangs after 2 seconds due to "too many packets". This is somewhat like the message which Xine player gives when trying that..

---

### Post by ahaslam on 2006-10-03
Have you got libdvdcss2 installed?
If not see here: [https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9](https://help.ubuntu.com/community/RestrictedFormats#head-38508785e53c611dde1859232189b2e823135eb9)

Tony.

---

### Post by KingFuzz on 2006-10-03
Yes, I've installed the restricted formats via Automatix, and doublechecked them through synaptic and your link. So I'm pretty sure alle libs are installed..
Thank you very much for you help so far, it's really nice of you to help a noob like me..

---

### Post by ahaslam on 2006-10-03
Did you also scroll down a little in that link & look at the region code & DMA info?
Your graphics are also worth considering, type **glxinfo** into a terminal, you'll see: 'direct rendering: Yes' near the top if hardware acceleration is enabled.

Failing this I wont be able to advise further, don't give up though I still consider myself a noob ;)

Tony.

---

### Post by KingFuzz on 2006-10-03
I read a bit about the region code, and the drives region is set to the right  region. I booted into windows to make sure and playback is working there. I read that DMA is enabled as default for drives that supports it in dapper, so that shouldn't be an issue (allthought I wouldn't know).

But I think you found my problem:
glxinfo says:

direct rendering: No

So know i just have to find out how to enable this on my card (S3 ProSavage DDR).
I'm still a bit puzzled that totem doesn't even see that there is a DVD in the drive. It should, at least be able to find it, eventhough it isn't able to play it.

Thank you for your help so far, you've been very helpful :)

-Chris

---

### Post by KingFuzz on 2006-10-03
A quick update..

After fondeling my xorg.conf and reading a couple of post here my screen is sharper than ever and direct rendering have been enabled. So now it's possible to watch silky smooth dvd playback in Mplayer.
Still nothing in Totem, though..
Thank you very much for your help, Tony, I'm very grateful..

-Chris

---

### Post by ahaslam on 2006-10-04
No probs, nice to help.

Don't give up, totem-xine is an excellent dvd player. Make a post specifically on Totem & hopefully someone will be able to help.

Tony.

---

