---
title: "Dell Precision M4300, sound gets louder and louder"
date: 2008-02-02
forum: Dell  Ubuntu Support
---

### Post by Abigail on 2008-02-02
I've got Gutsy running on my Dell Precision M4300 and sound works fine in general (playback & recording) but I'm having volume control issues.  The multimedia keys work and are bound to the ALSA master track; the following applies no matter whether I use them, the Gnome volume-control applet, or alsamixer.

If I turn the master volume slider down to, say, 50%, actual volume immediately drops to that level... but then it gradually increases back to full blast.  The slider doesn't move, just the sound gets louder and louder.  Even if I turn the volume all the way down to zero, it's back up at full blast within 40-50 seconds while the slider stays at zero.  Clicking/pressing "mute" doesn't appear to affect it at all.

Unfortunately that's all the troubleshooting I know to do.  Sound in Linux has generally "just worked" for me before, so I've never had to learn much about it.  Any suggestions what next?

---

### Post by thgys1245 on 2008-02-09
Getting the same problem (first noticed it playing Wormux but same thing happens in VLC player).  I've got a Dell Latitude D630 and the audio is SigmaTel C Major HD Audio.  I got the driver from the SigmeTel driver from Realtek.

There's got to be some connection because we're both running Gutsy on a Dell, and we likely have similar audio hardware.

---

### Post by LiquidIQ on 2008-02-09
Move the "Front" slider instead of the Master slider. Keep the Master at 100%, but adjust the Front to your specified level.

You can also upgrade to the latest ALSA and it won't have this issue.

---

