---
title: "no sound after update"
date: 2006-06-18
forum: Desktop Environments
---

### Post by Icaros on 2006-06-18
Updated the kernel and a few other things today and now I have no sound...  It was set on alsa previously and worked, and it's still set as alsa currently but it stopped working.  *shrug*

---

### Post by Icaros on 2006-06-18
weird... messing around with Beep Media Players output settings to see what I can find.  If I click on Preferences on my "ALSA 0.9.7 output plugin", I see the following in the drop down menu:

Default PCM Device (default)
Intel ICH5: Intel ICH5 (hw:0,0)
Intel ICH5: Intel ICH5 - IEC958 (hw:0,4)

Don't know why there are 2 of the Intel's now, but when I click on the 0,4 one, the song will play and I can see effects showing its playing, but I still don't get any sound.  No errors now though when I try to play a song, just no sound either...

---

### Post by kufford on 2006-06-18
I had the same problem, booted into windows to verify it wasn't hardware, and when i got back to dapper - it was back. ???

Try it and see...

---

### Post by Icaros on 2006-06-18
Tried that, didn't work...  Where can I configure my sound options again?  I thought there used to be some multimedia option that could do that (aside from the speaker icon next to the time) but I can't find it under admin or preferences.

---

### Post by xprisoner on 2006-06-19
I have the same problem. I updated a few days ago and sound quit working in most of my games. If I boot to my old kernel it works perfectly. Not sure if I just need to recompile some package or what.

---

