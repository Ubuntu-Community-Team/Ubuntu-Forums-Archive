---
title: "Sound Issue With Line In"
date: 2009-01-15
forum: General Help
---

### Post by drjonze on 2009-01-15
Hi,

I have an issue with the sound on my PC when using the line in on my sound card. The Line In channel seems to be coming in through the Master channel. I cannot mute or change the level of the Line In, I can only do that with the Master volume. This just suddenly happened last night. (The only change I made to my system was to install the 'New Style Last.Fm Plugin' for Rhythmbox.)I have tried all of the various mixers and have eliminated the possibility that line in is coming through a different channel through trial and error.

I tried the pulse audio configuration fix found here: [http://ubuntuforums.org/showthread.php?t=789578&highlight=pulse+audio]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulse+audio") but after doing that, I had no sound at all coming from the line in. I then reset my sound configuration, using this method: ```
sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2
```. This got the sound on my line in back but the original issue is still there.

I'm running 8.10 and I have an Nvidia HD sound card with a Realtek chip. 

Sorry for the long post and if my terminology is wrong or confusing!

---

### Post by drjonze on 2009-01-15
Bump

---

### Post by KeyserSoze93 on 2009-01-15
You could try recompiling ALSA:
[https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/156580/comments/10](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/156580/comments/10)

---

### Post by drjonze on 2009-01-15
> **KeyserSoze93 said:**
> You could try recompiling ALSA:
[https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/156580/comments/10](https://bugs.launchpad.net/ubuntu/hardy/+source/linux/+bug/156580/comments/10)


Thanks for the tip but it didn't work.

---

### Post by HyperHacker on 2009-01-15
I take it you've tried uninstalling that new plugin?

---

### Post by drjonze on 2009-01-15
I don't know how to do that

---

### Post by drjonze on 2009-01-15
Solved!

I again reset my sound configuration back to defaults and rebooted and disconnected/reconnected the plug from the line in. Then I went through the process of elimination with the asla mixer again and to my amazement, I could independently control the levels for my line in again - but its the CD track. Doesn't make a difference to me, as long as it worked!

---

