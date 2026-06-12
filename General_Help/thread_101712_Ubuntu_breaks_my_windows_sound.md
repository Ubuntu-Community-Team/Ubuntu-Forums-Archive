---
title: "Ubuntu breaks my windows sound"
date: 2005-12-10
forum: General Help
---

### Post by mhs on 2005-12-10
yeah it does ( i have Sound blaster extigy )
couple dayz ago i installed ubuntu .. then i wanted to go check out somethings in windows and i realized  i didnt have any sound// i tried all kinds of stuff to fix it (reinstalling drivers un-mute etc) but non of this woked ..
so i had to reinstall the whol system again..
and guess what it worked  ;///
no i loaded the ubuntu live cd cause i wanted to get my project from the old hd 
and guess what happend when i came back to win system ;p
i have no sound ~!!!

i posted this here to let the ubuntu geek squad know about this issue ;/
ggkthx

---

### Post by Sjneuzel on 2006-11-08
> **mhs said:**
> yeah it does ( i have Sound blaster extigy )
couple dayz ago i installed ubuntu .. then i wanted to go check out somethings in windows and i realized  i didnt have any sound// i tried all kinds of stuff to fix it (reinstalling drivers un-mute etc) but non of this woked ..
so i had to reinstall the whol system again..
and guess what it worked  ;///
no i loaded the ubuntu live cd cause i wanted to get my project from the old hd 
and guess what happend when i came back to win system ;p
i have no sound ~!!!

i posted this here to let the ubuntu geek squad know about this issue ;/
ggkthx
Did you ever had a sollution for the problem you described? Because yesterday I installed Ubuntu (edgy) for the first time. And when I switched back to Windows, the sound did not work anymore! I also use the Sound Blaster Extigy...

---

### Post by Intertricity on 2007-02-28
This is a bit hokey, but it worked for me.

In your linux install (where I assume the extigy is working), play something, and then yank out the usb and power.

Leave it out until you go back into windows.

Plug it back in when windows starts up.


I believe what's happening is that when linux shuts down, it seems to be turning off the sound card as well.

---

### Post by PaulFXH on 2007-02-28
I have a Sound Blaster Live card and I have had apparent sound loss quite a number of times particularly after a re-install or an upgrade.
**Invariably**, the problem has been rectified by typing this in terminal:
```
alsamixer
```
and then making sure that EVERYTHING  in the GUI that appears is unmuted and with a 50-100% setting (use the "M" key to toggle between mute and unmute and the up-arrow key to increase the volume settings).
Although I said "everything", in my case Analog/Digital Output Jack **must be muted**. Also, to avoid hearing your own voice it's best to have Mic Boost muted as well.
Well, that's what works for me. Who knows, maybe it'll solve your problems too.
Good luck.

---

