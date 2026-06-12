---
title: "No sound in 12.04 LTS"
date: 2012-06-05
forum: Desktop Environments
---

### Post by gl0w on 2012-06-05
Hello guys, 

I'm rather new to Linux, but after installing Ubuntu - liked it right away and wanted to learn. The problem I was having after the install was no sound. After I used the awesome power of google, not only do I have no sound - I have no speaker icon on the top bar. I tried installing restricted extras and drivers, tried other things I half understood but looked promising.  I probably posted this wrong and in the wrong place.. But I've abandoned all hope now.. 

Would be very happy if my cause could be helped.. What logs/info should I provide?

Thanks in advance

---

### Post by IWantFroyo on 2012-06-05
Try running this in Terminal:
 
```
alsamixer
```
 
It's possible that your sound is muted. Hit m to unmute a channel.

---

### Post by gl0w on 2012-06-05
thanks for the reply!

I did run alsamixer somewhere in my endeavours, this is what I have now:
 
every single channel unmuted (OO)

ALSA Driver version 1.0.24
/asound/cards : 0 [PCH   ]; HDA-Intel - HDA Intel PCH

---

### Post by gl0w on 2012-06-05
Ok, so the sound is there now, and I'm eternally thankful!

But the sound icon in the top menu - how do I get that back?

---

### Post by IWantFroyo on 2012-06-05
This is where I got stuck. I just moved to gnome-shell. I think there might be a way to edit the top panel though. Try holding ctrl-alt-shift while right clicking. You might be able to add it. I can't remember the precise keyboard shortcut, however. Might be alt-shift.

---

### Post by gl0w on 2012-06-05
Nope, no luck.. But this I can live with for now. Thanks a lot!

---

