---
title: "Beep sound changed in 9.10"
date: 2009-11-10
forum: Desktop Environments
---

### Post by Arndt on 2009-11-10
I'm not sure if this is the best forum for this question, but we'll see.

I just upgraded from 9.04 to 9.10, and this went mainly without problems. One thing that changed was the sound of alerts, namely

1) The sound emitted in the shell when I for example type the beginning of an ambiguous filename and then press Tab, and also the sound emitted by Emacs when using for example Ctrl-G.

2) The sound emitted when Firefox presents an alert box, such as the one when I do File->Quit.

1 used to be a beep or honk like sound, probably the default sound from the computer (Lenovo Thinkpad 300). I don't remember what 2 used to be, maybe nothing at all.

Now, 1 has changed to something like a discreet "tick", while 2 is a "drum" sound similar to what I get (got - I turned it off) when booting 9.04.

I don't like these sounds for these purposes. Especially the tick is hardly audible. How can I get the honk or beep back?

---

### Post by Arndt on 2009-11-12
bump

---

### Post by Arndt on 2009-11-14
bump

---

### Post by kostkon on 2009-11-14
Yeah, the *pcspkr* module (the driver for the pc speaker) is blacklisted by default on 9.10 and now the warnings/event sounds are played through *PulseAudio* (using *libcanberra* I think). Why it was disabled? Check [here]("https://bugs.launchpad.net/hundredpapercuts/+bug/290204").

Anyway, you could disable the event sounds in your sound preferences and then re-enable the *pcspkr* module.

To re-enable it, although don't take my word for it, I don't really know if it is valid on 9.10, try this:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
and you should find a line
```
blacklist pcspkr
```
Just delete it.

---

### Post by Arndt on 2009-11-18
> **kostkon said:**
> Yeah, the *pcspkr* module (the driver for the pc speaker) is blacklisted by default on 9.10 and now the warnings/event sounds are played through *PulseAudio* (using *libcanberra* I think). Why it was disabled? Check [here]("https://bugs.launchpad.net/hundredpapercuts/+bug/290204").

Anyway, you could disable the event sounds in your sound preferences and then re-enable the *pcspkr* module.

To re-enable it, although don't take my word for it, I don't really know if it is valid on 9.10, try this:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
and you should find a line
```
blacklist pcspkr
```
Just delete it.

Thank you, I will try that next time I reboot. But if it just did what it says it should " this should be done by a nice pulseaudio bing", I would have no complaints. It's just that the sound played now is a pathetic little 'tick'. Where can I configure those sounds?

---

### Post by AJROKR on 2009-11-18
I had some serious trouble with 9.10 (Dont know 32 or 64) must be 32..

My 9.04(32bit) was working perfectly with my laptop along with XP( I have dual os)

Two days back i updated to 9.10 from 32 bit 9.10 and facing problem since then.

Everything is working perfectly except one...and i.e. i am not able to shutdown the system completely

Then i had to remove ubuntu from my laptop. i dont mind making my laptop to run only ubuntu...please help on this 
My system is Levnovo core 2 duo, 1 GB RAM ,160 GB SATA, DVD RW etc etc. Model no 77579RQ

The message i got was this....during shutdown...

Stopping ClamAV Virus databse update freshclam
Shutting down ALSA
Asking all remaining process terminate
Deconfiguring network interface
Deactivating Swap
1635.324526 Buffer I/O error on device loop0, logical block 2137453

What i have to do to rectify this.....

Looking forward for your reply...

---

### Post by Arndt on 2009-11-18
> **AJROKR said:**
> I had some serious trouble with 9.10 (Dont know 32 or 64) must be 32..

My 9.04(32bit) was working perfectly with my laptop along with XP( I have dual os)

Two days back i updated to 9.10 from 32 bit 9.10 and facing problem since then.

Everything is working perfectly except one...and i.e. i am not able to shutdown the system completely

Then i had to remove ubuntu from my laptop. i dont mind making my laptop to run only ubuntu...please help on this 
My system is Levnovo core 2 duo, 1 GB RAM ,160 GB SATA, DVD RW etc etc. Model no 77579RQ

The message i got was this....during shutdown...

Stopping ClamAV Virus databse update freshclam
Shutting down ALSA
Asking all remaining process terminate
Deconfiguring network interface
Deactivating Swap
1635.324526 Buffer I/O error on device loop0, logical block 2137453

What i have to do to rectify this.....

Looking forward for your reply...

I sympathize, but don't hijack others' threads. Start a new thread of your own.

---

### Post by Arndt on 2009-12-10
> **Arndt said:**
> Thank you, I will try that next time I reboot. But if it just did what it says it should " this should be done by a nice pulseaudio bing", I would have no complaints. It's just that the sound played now is a pathetic little 'tick'. Where can I configure those sounds?

No, changing blacklist.conf didn't help.

---

