---
title: "Wireless Gone After Reboot"
date: 2006-03-13
forum: Desktop Environments
---

### Post by schnarff on 2006-03-13
OK, this is a really, really weird one, so bear with me here while I lay out exactly what happened.

I've had PCI-based wireless working on my Breezy AMD64 system via ndiswrapper for a few months now. It doesn't start properly at boot, but that's a minor issue that I haven't bothered to fix. Just now, I shut the system down, swapped out a video card and ran Memtest on a couple of sticks of RAM, so that I could sell all of that stuff on eBay; when it all looked good, I put the box back *exactly as it was before* and booted up. Much to my dismay, when it came up, my wireless card had completely vanished.

My first thought was that the updates I had run just before the reboot -- which looked like they included kernel foo -- had torched the wireless, so I rebooted on the previous kernel; no luck there. On the off-chance that the motherboard was getting wonky on me (it's new as of December), I ran "lspci -vv"...and much to my dismay, there was no apparent sign of my wireless card. Looking back at my old dmesg's from /var/log/messages.*, I noticed that ndiswrapper had been bringing the card up via IRQ 18; now, it looks like some other device has taken that IRQ.

I'm at a real loss here. It's not like I updated my BIOS, changed any settings therein, or even changed hardware, so it's not like I should have had any IRQ reassignments going on. At the same time, to the best of my knowledge, OS updates shouldn't muck around with IRQ settings. That said, does anyone have any idea what could have possibly occured here? Did any of the recent package updates on Breezy torch other peoples' wireless? Any thoughts on what the heck I could do to get things back up and running?

Thanks,
Alex Kirk

---

### Post by Titus A Duxass on 2006-03-14
I had a similar problem and a crazy fix.

Shutdown but do not unplug the pc, pull the wireless card out, reboot.
When able, shut down again, do not unplug, reinstall wireless card and reboot.

That cures my similar problem.

---

### Post by schnarff on 2006-03-14
Crazy, but perfectly feasible. I'll let you know if it works later tonight, when I'm at home with the machine.

Thanks!

---

### Post by schnarff on 2006-03-16
That worked like a charm! I was going to post a thank-you last night, but the forums were offline. Anyway, I really appreciate the pointer -- I wouldn't have thought of that for quite a while, and this saved me lots of hassle. Thanks!

Alex Kirk

---

### Post by Titus A Duxass on 2006-03-16
You're welcome.
I have to repeat the exercise every time I disconnect the PC from the Main Supply (ie. unplug it).
I think it has (in my case) something to do with the Edimax EW-7126 card.

My other pooter with a T-online 154pci card does not have the same problem.

Am pleased it helped.

Grüß aus Buxtehude

---

