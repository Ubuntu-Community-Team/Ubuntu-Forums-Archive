---
title: "Kernel Panics - Desktop, not wireless, multiple Ubuntu versions"
date: 2009-01-21
forum: General Help
---

### Post by kendallp on 2009-01-21
First off, I would like to apologize for things I leave out or get incorrect.  I have used linux for 5+ years but know just enough to get around.

I first started using Ubuntu 7.04 around July 2007.  I upgraded to 7.10 and have since upgraded to 8.04 and have also tried rolling back to 6.06 and with all versions I have had issues with intermittent kernel panics/freezes/reboots.  I can sometimes go a week or two without a crash (with computer usually turned off every night, sometimes left on for a couple days at a time) or sometimes I have days like yesterday when I had a panic every time I started Firefox and today where I had a panic right after turning on the machine and logging in.


**Here are hopefully all the computer hardware questions you need answered:**

Asus ASN8X-E Deluxe Motherboard (latest BIOS)
AMD Athalon XP 3200
2 GB Corsair memory (2x1 CMX1024-3200PRO)
XFX Nvidia GeForce 7800 GT
Additional NIC - 3com 3C509B
Main HD running ATA, storage HD on SATA

For the Nvidia drivers I have tried the default Ubuntu drivers, Envy, and currently am using the drivers available from Nvidia's website.

I have let MemTest run overnight with no errors.

All of my fans in my case/processor/video card are working.  I do not think overheating is an issue because sometimes they happen as soon as I turn the machine on and login.

I am not using a wireless card.

I use the machine for my firewall/NAT, some additional storage, web surfing, occasionally UseNet file downloads.


**The problem:**

As I said before it is very intermittent.  I sometimes have desktop crashes (rare) where Ctrl-Alt-Bckspce brings me back to the login screen.  Occasionally Alt-SysReq-r+s+e+i+u+b works.  Most common though is a hard lock where the only thing will work is using the reset button and the majority of the times the hard lock includes the flashing Caps Lock & Scroll Lock keys.

I can never make this happen but when it does happen it is usually when I am surfing the web and especially when videos are present (i.e. YouTube).  Sometimes it will happen while the machine is left on overnight (rare) and I can not ever think of a time it has happened when I was not logged in to the desktop (sitting at the login prompt).

I am using a pretty standard Ubuntu install with no real additional installed programs minus Arno's IPtables firewall.

I have tried multiple suggestions I found via searches on the Ubuntu forums and also through Google, the latest was turning off the Powernowd service.


**What to do?**

Trying to logically decide how to proceed without throwing my computer out the window, I narrowed it down to two possible solutions (I think).  Either try another distro or try my hand at building a custom kernel.  I was leaning to the custom kernel (because I am lazy and don't want to have to set everything up again) but found a few posts that I inferred the process most likely won't fix my problem.

So I am humbly before you, the Ubuntu community, asking for suggestions.

Thank you very much for the patience of reading through this post and I look forward to any responses I can get.


Thank you,
-Kendall

---

### Post by RJARRRPCGP on 2009-01-21
Maybe the capacitors on your motherboard or power supply went bad on you:

[http://badcaps.net](http://badcaps.net)

---

### Post by kendallp on 2009-01-21
I do not think that is the issue because of the sometimes rarity of the issue.  I've had a motherboard with bad caps before and it would never go a week or two without a crash.

Thanks for the suggestion though.

---

### Post by Crafty Kisses on 2009-01-21
Usually kernel panics are due to bad/faulty hardware. I'd have to say check your RAM, if your computer freezes while your doing something on the Internet, like watching videos, it really could be a RAM issue. It really all depends, if you feel like building a newer kernel would help, you could try that too.

---

### Post by RJARRRPCGP on 2009-01-21
You may need to clean your heatsink.

---

### Post by kendallp on 2009-01-21
I will rerun MemTest overnight and tomorrow while at work then when I get home I will replace my heatsink (not overclocking so I have an extra factory AMD heatsink I can try).

I will keep everyone updated and thank you again for the suggestions.


-Kendall

---

### Post by Crafty Kisses on 2009-01-21
Yes please keep us updated, run memtest, and see if that gives you any different results from last time.

---

### Post by kendallp on 2009-01-22
As a minor update:

MemTest86+ ran overnight, 7 or 8 passes, without an error.  I left it running while I am at work but am pretty sure bad ram can be taken off the checklist of possible issues.

I will still replace the CPU heatsink tonight and will also do a once over on the board to check for bad capacitors.  Can't hurt to look.


Thanks,
-Kendall

---

### Post by kendallp on 2009-01-22
MemTest86+ results:

Wall Time: 17:44:02
Pass: 16
Errors: 0

So ram issues should be out.


I switched the CPU heatsink and will monitor lm-sensors.


2 points to RJARRRPCGP, at least one leaking capacitor.  With the age of the board and cost to replace the capacitors (because I suck at soldering), if I continue to see problems, a new computer is the next stop.


Thanks again for the help,
-Kendall

---

### Post by Bakon Jarser on 2009-01-23
Hmmmmmm........probably just a coincedence but I'm having the same problem that just started today and am running an Asus a7n8x deluxe.  It probably is just old hardware.  I also passed the memtest86 and all the temps seem to be okay.  The PSU is only a couple months old.

Asus a7n8x deluxe
amd athlon 2500+
nvidia mx440 (using the 96.x nvidia driver)
1gb corsair ddr400
chaintech a710 sound card
80gb ata hd
500gb sata primary hd
anantec psu
ubuntu 8.10

---

### Post by Bakon Jarser on 2009-01-23
At least one other person with my motherboard has had this problem.

[http://ubuntuforums.org/showthread.php?t=832383](http://ubuntuforums.org/showthread.php?t=832383)

post 147

---

### Post by kendallp on 2009-01-23
Well I used the box for a few hours last night (websurfing) with no issues.  The biggest reason I have dealt with the problem so long is it is so intermittent that it rarely continuously frustrates me.  I'll have a bad day, then nothing for a week.  The only reason I finally posted is I had two days in a row of problems and I finally got fed up (but am slowly forgetting already).

On to the Asus A7N8X board.  I think Asus had a run of these where they used cheap capacitors.  A year and a half ago I replaced one of these boards because of bad capacitors.  With socket A parts becoming rare (and therefore expensive), I don't think it is worth repairing anymore.  For the price of a new/used socket A board (well one that has things like SATA on it) you can buy a new entry level board with much superior technology along with the new processor.


-Kendall

---

### Post by Bakon Jarser on 2009-01-23
Yeah, I really don't need much more power but it looks like I can get an asus board with onboard nvidia graphics, 1gb ram, and a processor better than the one i've got for $130.  I guess it's time to bite the bullet.  I don't blame asus, they've been a really good company in my experience.  Six years and this is the first time I've ever had a problem.  I may even replace the capacitors to have a backup system.

---

### Post by kendallp on 2009-01-23
Just turned the machine on, loaded yahoo.com and the computer frooze with flashing Caps Lock and Scroll Lock.  Ohh well, guess it's time to bite the built here also.


-Kendall

---

