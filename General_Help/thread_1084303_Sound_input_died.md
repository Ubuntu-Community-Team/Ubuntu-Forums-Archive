---
title: "Sound input died"
date: 2009-03-01
forum: General Help
---

### Post by billjoie on 2009-03-01
I had ubuntu 8.10 and the whole sound was great.  I had removed pulseaudio and replaced it by esound in order for skype to work, but that was a long time ago.  Then, the sound-in stopped working altogether, on skype or gnome-sound-recorder.  I can still play music and everything, but not record anything.  The only thing that has changed that I can think of is that I installed Xubuntu as a second desktop.  I use AlSA, but also tried OSS.

I have checked that nothing is muted on amixer, all my volumes are up.  I have played forever with the multimedia-selector and the sound in the preference menu, testing each time with sound-recorder and skype. I have removed all traces of Xubuntu.

I have upgraded the distro to ubuntu 9.04 (partly for the fun of it), but the problem remains.  Can anyone help?  Any diagnostic ideas?  Google has me searching in circles on this.

---

### Post by billjoie on 2009-03-02
After attempting many useless things, changing the channel mode from 6 channels to 4 channels solved all my problems.  Anyone understands what the fundamental difference is, and what might have lead to these channel settings to be changed?  Thanks in advance, comprehension is valuable in linux...

---

