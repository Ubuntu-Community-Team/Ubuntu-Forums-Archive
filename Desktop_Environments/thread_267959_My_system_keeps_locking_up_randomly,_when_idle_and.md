---
title: "My system keeps locking up randomly, when idle and when in use"
date: 2006-09-29
forum: Desktop Environments
---

### Post by jonread1983 on 2006-09-29
Hey :)

I have a problem, and being fairly new to Linux its hard for me to find the info i need for people to help me :confused: :confused: :confused: 

My problem is this:

My system keeps locking up, seemingly for no reason. Once was while playing OpenTTD, the other i was on my desktop.

When the crash occours the symptoms are the same, the mouse stops moving, the keyboard becomes unresposive. When on desktop the clock doesnt advance, I cant tell whether its a GUI crash, or a complete system lockup. The only was out is a hard reboot. :(

Any ideas how i could find whats causing this? I dont suspect it to be the RAM im pretty sure its a software fault.

Cheers

---

### Post by macogw on 2006-09-29
This has been happening to me.  I think it's a driver problem.  My syslog says this:

Sep  7 16:42:19 localhost kernel: [17180054.844000] ide: failed opcode was: unknown
Sep  7 16:42:19 localhost kernel: [17180054.844000] hda: DMA disabled
Sep  7 16:42:49 localhost kernel: [17180084.844000] hda: ATAPI reset timed-out, status=0x90
Sep  7 16:43:24 localhost kernel: [17180114.844000] ide0: reset timed-out, status=0x80
Sep  7 16:43:24 localhost kernel: [17180119.848000] hda: status timeout: status=0x80 { Busy }
Sep  7 16:43:24 localhost kernel: [17180119.848000] ide: failed opcode was: unknown
Sep  7 16:43:24 localhost kernel: [17180119.848000] hda: drive not ready for command
Sep  7 16:43:54 localhost kernel: [17180149.848000] hda: ATAPI reset timed-out, status=0x80
Sep  7 16:44:24 localhost kernel: [17180179.848000] ide0: reset timed-out, status=0x80

A bit of research says ATAPI is a an optical drive driver.  So, it seems like there's some sort of miscommunication between the hard drive (hda), optical drive (ide0) and the necessary drivers to get the motherboard to recognize them.

My boyfriend's going to take a look this weekend.  If he figures anything out, I'll let you know.

---

### Post by jonread1983 on 2006-09-29
Interesting. I'll examine my syslog after the next crash and post the logs leading up to it.

Cheers :D

---

### Post by macogw on 2006-10-05
editting the BIOS to reflect that I am not on Win XP/DOS did not help.  [http://ubuntuforums.org/showthread.php?t=261663](http://ubuntuforums.org/showthread.php?t=261663) This thread, however, is about the cd drive randomly opening up (which mine does).  Given that the cd drive is referenced in the syslog when I crash, I mentioned that in there.  Foxxx suggested taking out the cd drive (if you're on a desktop, disconnect the cables) and rebooting.  I'm going to try it.

---

### Post by macogw on 2006-10-09
Well, I called Gateway and they said it sounds like a mobo problem, so I'm sending it in to have the mobo replaced.  I should've recognized that the randomly turning off speakers, crashing, cd rom drive, overheating, fan not spinning (well that'd explain some of the heat...), etc. all adds up to 1 bad motherboard, not lots of crappy little pieces.

---

### Post by jacob.pederson on 2007-07-26
Hi, been using Ubuntu for years now, and this is the first time I've had problems with it.  Suspect motherboard/chipset driver issue.  Here is why.  I have the exact same symptoms as you, and what we have in common is the motherboard.  Had a bunch of old socket A chips laying around, so picked up the m848a to try and get some use out of them.  Big mistake it appears.

Interesting thing is that this issue seems to only be with Ubuntu.  So far I've tried extensive burn-in tests on my Windows PE disk, and on a Knoppix disk (also Debian).  No problems or crashes there.  Don't chase the hardware if you have this issue!

-Jake

---

### Post by macogw on 2007-07-26
Actually, this stopped happening when I upgraded to Feisty in January (the alpha).  The problem is there in Debian Stable (Etch) now though.


Oh, Gateway's fix was reinstalling Windows.  My lappy was also overheating though, and what fixed that was putting some thermal paste on (because the stuff Gateway put on had hardened and therefore wasn't doing anything)

---

