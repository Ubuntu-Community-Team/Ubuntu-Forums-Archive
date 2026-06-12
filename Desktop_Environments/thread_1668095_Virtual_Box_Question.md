---
title: "Virtual Box Question"
date: 2011-01-15
forum: Desktop Environments
---

### Post by throese on 2011-01-15
So, why is it that operating systems, especially Windows OSes run so much faster in Virtual Box than if they were actually on the hard drive, fresh install either way.

---

### Post by Timmer1240 on 2011-01-15
Yes Mine are pretty quick in virtual box windows xp runs good there but I keep it lean and mean!

---

### Post by throese on 2011-01-15
But what I'm asking is, why is it so much faster on VB compared to being a fresh install on the actual Hard Disk Drive?

---

### Post by 1clue on 2011-01-15
You're seeing something that's misleading.

Virtual machines technically run slower.  But the thing is, the hardware seen by the virtual machine is not the actual hardware.  It's a driver on top of a driver, to look like a single piece of hardware that represents, say, a disk drive.  That way they only need to implement one driver.

Likewise, that disk drive doesn't actually have to do things like fsck during VM boots because that was already done when your host system booted.  Disk scans, formats, checks, etc all happen incredibly fast because the virtual machine software knows what's happening and short circuits it because it's irrelevant.

---

### Post by throese on 2011-01-15
Oh, I didn't know that. Cool, but is it bad that it short circuits things it already knows?

---

### Post by 1clue on 2011-01-16
Not really.  You can still fsck manually if you crashed, but a virtual machine disk is not a spinning platter with magnetic dust on it.  It's a file on a hard drive, a filesystem inside a filesystem.  The functions associated with preserving disk integrity are on your host system.

I learned my VM stuff on VMware.  They have pretty good explanations of all that, and I'm sure VirtualBox has it too, to explain the rationale.  It's past bedtime right now so I doubt I could be clear enough to make sense.

---

### Post by 1clue on 2011-01-16
Oh yeah!

When a hardware machine crashes you get a good chance of disk damage.  When the VM crashes, you have your virtual machine software still hanging around to take care of flushing files and whatever else needs to be done.  Less chance of virtual disk damage.

---

### Post by throese on 2011-01-16
Interesting and cool. =)

---

### Post by slooksterpsv on 2011-01-16
Another reason why it may seem faster is cause with like Vista or 7, it, by default, doesn't do the DWM - Desktop Window Manager (for the special transparent effects) - so that's disabled by default.

Also, I've found a lot of the HP drivers are bloated, some of the drivers that are provided with standard installations are bloated themselves for "extra" functionality.

As was stated before, it's a perceived performance increase, but technically there isn't a performance increase.

---

### Post by throese on 2011-01-17
Ah, now it all makes sense. Acer Aspire 5100 is what I have. Was originally my dad's in 2006 which is when he first bought it.

---

