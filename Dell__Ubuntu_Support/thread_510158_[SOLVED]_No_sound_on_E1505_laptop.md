---
title: "[SOLVED] No sound on E1505 laptop"
date: 2007-07-26
forum: Dell  Ubuntu Support
---

### Post by jpmallory on 2007-07-26
The sound on my laptop stopped working two days ago after a reboot.

Prior to the reboot, I had done a couple of things.

Ran updates.
Installed Virtualbox.

I suspect the former over the latter.

I'm not very well versed in troubleshooting drivers in Linux, yet...

I was going through the guide listed here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

I tried this:

$ aplay -l
aplay: device_list:222: no soundcards found...

Ok, so I did this: 
$ sudo lspci -v
...
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell Unknown device 01bd
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0
...

Then it suggested I search for an existing ALSA driver for the device, which I think I did.
So in the next step, I tried this:

$ sudo modprobe snd-hda-intel

Which returned nothing.  I tried 'aplay -l' and got the 'no soundcards' message again.

Any suggestions or help on this is appreciated.

Jason

---

### Post by HeavyAl on 2007-07-26
Though I hope it's just a software issue, there were some threads around here talking about how the headphone jack on the 1505 series would sometimes come loose and cause the entire sound system to quit functioning. Some people were saying that if you just jiggle the headphone port a bit it would come back to life, others were saying that sending it back for repair was the only way to deal with the problem. 

If I find the threads regarding this I'll post back...

---

### Post by jpmallory on 2007-07-26
That's interesting.  I hope it's just a software issue too.  Otherwise it will be the second time I've had to ship the laptop back since I've gotten it.  The wireless nic was broken right of out the box.

I've tried compiling the driver myself, but it failed.  I'll post more about the error I'm getting doing that in a bit.  Right now I'm backing up all my stuff, as I may just say "screw it" and wipe the system back to defaults, and see if the problem persists.

---

### Post by DonA on 2007-07-26
I'm one of those whose speaker sound just quit one day, after working perfectly.  Sound at the headphone jack was fine, but no amount of jiggling the connector would send sound to the speakers.  The same symptoms were seen with the Live CD, so the config on the HD install became less suspect.  After a call to the Dell/Ubuntu hardware support line, I sent my E1505n back for repair.  The note from the technician indicates that the system board and the speakers were replaced.  I don't know if both were bad, or if they were just "shotgunned".  At any rate, after the repair, my speaker sound is back, and I'm enjoying it a lot.

Good luck.     ..DonA

---

### Post by jpmallory on 2007-07-27
Well, I ended up restoring the system back to factory defaults.  Sound works great now.

My only regret is not having more patience and fixing the problem myself, as I'd like to know what to do if it happens again.

---

### Post by johnn1949 on 2007-07-28
I bought an E1505 in Dec 07,  When I received it one channel of sound did not work.  After extensive chat, I got someone who said the motherboard was bad and it was replaced.  This all was while using Windows XP.

---

### Post by jpmallory on 2007-08-11
Turns out, I'm a dumbass.

The reason the audio quit is that I had removed myself from the 'audio' group through erroneous use of the 'usermod -G' command.

I didn't know there was an audio group until this morning.  As a test, I removed myself from the group and rebooted.  No audio.  Added myself back, and the audio works.

---

