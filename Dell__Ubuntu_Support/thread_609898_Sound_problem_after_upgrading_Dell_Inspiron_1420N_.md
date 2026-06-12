---
title: "Sound problem after upgrading Dell Inspiron 1420N  to Gutsy Gibbon 7.10"
date: 2007-11-11
forum: Dell  Ubuntu Support
---

### Post by LisaM on 2007-11-11
Hi, I recently upgraded from 7.04 to 7.10 and now am having trouble with the sound on my Inspiron 1420N. If I lean up close, I think I can hear sound through the headphone jack, but nothing from the speakers. Also, the SD cards are not recognized now. Can anybody help?

Thanks!

 Lisa

---

### Post by ajopaul on 2007-11-11
type > ```
gnome-volume-control
``` at the terminal and check if all the switches are non-mute and full.. and what does```
 lspci | grep audio
``` return ?

---

### Post by carnagex420x on 2007-11-11
The 1420 sound card works with ALSA. If you have the packages installed running "alsamixer" can help to.

---

### Post by LisaM on 2007-11-11
Everything looks fine when I type gnome-volume-control.   Also, everything looks fine in ALSA Mixer.

I get nothing but another terminal  prompt when I type lspci | grep audio

Any more ideas?

Thanks! 

Lisa

---

### Post by ctpaterson on 2007-11-12
> **LisaM said:**
> Everything looks fine when I type gnome-volume-control.   Also, everything looks fine in ALSA Mixer.

I get nothing but another terminal  prompt when I type lspci | grep audio

Any more ideas?

Thanks! 

Lisa

Actually, it needs to be "lspci | grep -i audio" for the command to be meaningful.

Cheers.

---

### Post by mdwy62 on 2007-12-22
Hi - I have the same no sound problem on the inspiron 1420 after upgrading to gutsy. The upgrade was through the Upgrade Manager.

the command: lspci | grep -i audio
returns: 00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

gnome-volume-control displays one of two devices, either of which can be selected from the File Menu.

The first is HDA Intel (Alsa mixer) - on the Playback Tab has a Master slider and two PCM sliders. I have these three all the way up. On the switches tab, there is "Line in as Output" and "Mic as Output" - neither of these boxes are checked.

The second device is a SigmaTel STAC9228 (OSS Mixer).  This only has a playback tab with one slider called "Volume" that is all the way up.


Thanks for any insights!

---

### Post by mdwy62 on 2007-12-22
> **carnagex420x said:**
> The 1420 sound card works with ALSA. If you have the packages installed running "alsamixer" can help to.

This did the trick - From alsamixer, there was a slider "Front" that was low. I set this up and I've got sound!

Thanks for the suggestion!

-Mark

---

