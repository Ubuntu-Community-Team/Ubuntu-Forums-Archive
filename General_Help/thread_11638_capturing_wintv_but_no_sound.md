---
title: "capturing wintv but no sound"
date: 2005-01-18
forum: General Help
---

### Post by tuco on 2005-01-18
I have an old wintv card that I can see and hear tv but when I try to record, I can't record the sound even though I hear the sound while recording using mencoder and nuvrec. I have used aumix, amixer and gnome's Volume control to set recording to Line1 (which I found out is where my wintv card is connected to for sound.) Is there something else I need to do inorder to record sound? Anything will be helpful. I was able to get this to work in Mandrake and Knoppix before.

thanks,
tuco

---

### Post by burok on 2005-10-25
I had this problem too couse i recorded sound from /dev/dsp but there is ALSA in Ubuntu and should record from /dev/audio.

look at my mencoder script
[http://www.ubuntuforums.org/showthread.php?t=68983](http://www.ubuntuforums.org/showthread.php?t=68983)

now it works for me :)

---

