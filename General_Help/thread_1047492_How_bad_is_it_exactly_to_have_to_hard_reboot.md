---
title: "How bad is it exactly to have to hard reboot?"
date: 2009-01-22
forum: General Help
---

### Post by Jameshardy88 on 2009-01-22
Hi ive got a problem with my laptop at the moment where it freezes randomly approximately once a day. I can't work out what the problem is but i think it is hardware related rather than anything to do with Ubuntu. Anyway that is a separate issue my question is how bad is it exactly to have to hard reboot my computer on a regular basis and what possible consequences may this create? and how likely are they to arise?

---

### Post by lykwydchykyn on 2009-01-22
The received wisdom is that its bad bad bad.

Though based on about 6 years experience installing Linux on dodgy machines that had hardware issues, I can safely say it's not really that likely to cause problems.  Modern Linux file systems have a journaling layer to recover from crashes like that, and I've yet to see one have major lasting problems from hard reboots.

Still, I'd want to fix whatever was forcing me to hard reboot.

---

### Post by philinux on 2009-01-22
Until your problem is solved dont hard reboot use this.

[http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

Hold down the two keys with your little fingers.

---

### Post by lukjad on 2009-01-22
It all depends on what is going on at the time of the hard reboot. Sometimes, it can do great damage, other times it can be hardly noticed. Simply put, it is best to not do it, if at all possible.

---

### Post by Jameshardy88 on 2009-01-22
> **philinux said:**
> Until your problem is solved dont hard reboot use this.

[http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php](http://lifehacker.com/software/linux-tip/gently-restart-a-frozen-system-298891.php)

Hold down the two keys with your little fingers.

i tired doing this (when not frozen) but nothing seemed to happen, well other than i got flooded with printscreens lol

---

### Post by Jameshardy88 on 2009-01-22
> **lukjad007 said:**
> It all depends on what is going on at the time of the hard reboot. Sometimes, it can do great damage, other times it can be hardly noticed. Simply put, it is best to not do it, if at all possible.

is it actually going to damage the computer though or just the software?

(sorry i realise that this is a pathetically basic question)

---

### Post by ajcham on 2009-01-22
> **Jameshardy88 said:**
> is it actually going to damage the computer though or just the software?

(sorry i realise that this is a pathetically basic question)

My assumption has always been that as long as you are using the power button on the front of the PC (the one which has to be held down for a few seconds) this sends a signal for the hard disk(s) to idle down and park the heads, meaning that although data loss or corruption could occur, the disk would be physically unharmed.

If, on the other hand, you completely and suddenly cut power - flipping the switch on the PSU or pulling the plug - then this could damage the harddisks if they are currently in the middle of a read/write operation.

I've never actually verified this assumption, so I may be completely wrong - it's quite possible that hard disks have some sort of failsafe mechanism to prevent physical damage in the event of unexpected power loss.  Someone more knowledgeable can almost certainly provide you with better information.

---

### Post by jerome1232 on 2009-01-22
I don't believe it could ever cause physical damage, One of my computers (win95 era hardware) is on 24/7 and has had power rudely cut to it 5 or so times (circuit breaks being flipped, power outages and etc..)

It's still kicking, just had to do a quick fsck after a reboot each time.

---

