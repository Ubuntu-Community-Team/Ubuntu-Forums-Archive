---
title: "Locking up and keyboard flashing"
date: 2008-04-22
forum: Desktop Environments
---

### Post by j00bhaka on 2008-04-22
Hello,

I just installed Ubuntu on my old desktop machine which has ran fine for the past 6 years.  After about 20 minutes of running, the machine locks up and the keyboard lights flash (caps lock and scroll lock).

I have to reboot to unfreeze it, but it will do the same thing each time.  It doesn't matter what I'm doing at the time.

I have tested the memory with memtest86+ and it did not show any errors.  I am running an AMD 2800+ with 512MB DDR1.

It seems like a kernel panic, but I searched the syslogs and cannot find anything in there.

Any help would be greatly appreciated!

j00bhaka

---

### Post by j00bhaka on 2008-04-22
It just happend again but this time the keyboard lights didn't flash -- they stayed off.  It happend when opening firefox this time -- but I'm not sure what the issue may be.

I have been watching the system monitor and nothing strange seems to be happening.  Any ideas?

---

### Post by Nimaran on 2008-09-06
Same problem here, randomly locks up with keyboard lights flashing. Nothing works, I have to press the power button and restart. Very weird, very annoying any help would be awesome!

---

### Post by The Spy on 2008-09-06
Yeah, it's happening to me as well on my desktop, but when I reboot, it sometimes doesn't even get to the login screen. I haven't had this problem at all, and I've been using Ubuntu for a couple year now. I have had my Powerbook g4 do the samething, but it was only a couple times, and always in the OS while I was doing something.
I don't recall my keyboard lights flashing, but I never looked, so...
I was thinking it might have been some wireless driver issue, so I removed my Linksys wireless card (from my desktop), but it still acted up.
The first time it happend I went into recovery mode, and also did a memcheck. The system seemed to lockup in recovery mode as well.

---

### Post by pbhj on 2008-09-06
> **j00bhaka said:**
> Hello,

I just installed Ubuntu on my old desktop machine which has ran fine for the past 6 years.  After about 20 minutes of running, the machine locks up and the keyboard lights flash (caps lock and scroll lock).


This is about the age at which power supplies often fail - they tend to fail by producing weird errors because they aren't quite putting out the right power. It could be that 20 mins in your fans need to speed up to manage the growing heat, they are speeded up and the resulting load means the PSU can't supply something else (the motherboard) properly.

It could also be a fan that isn't cooling properly and some sort of thermal cut-off is switching off the machine. You have fans in the PSU, on your processor, on the case and sometimes directed at the disk drives. Use a hoover to clean them - CAREFULLY - and don't touch the hoover to the components as it may be statically charged. Try having the case open with a deskfan pointing at it from close up and seeing if that cures it, if so then it's a heat issue.

My bet, PSU.

---

