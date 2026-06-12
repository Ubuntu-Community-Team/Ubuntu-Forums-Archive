---
title: "Dell Inspiron 15 (the 16:9 one) partitioning"
date: 2009-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by oddeyed on 2009-05-12
Hello. 
First Ubuntuforums post, this is all very exciting! Sorry if this is the wrong place to post this, but I couldn't find a Hard drive or Partitioning forum.

I've been an Ubuntu follower for years, and when I finally saved up the cash, I bought myself a Dell Inspiron 15 (a.k.a. 1545) with Vista (Dell stopped selling Ubuntu ones) and put Ubuntu straight on it. 

BTW: If you wanted to know, on 9.04 EVERYTHING worked out of the box perfectly (except I haven't tested the SD card reader). Only thing is that sometimes nm-applet doesn't detect that I switched of my Wifi card, so just keeps trying to connect. Oh and multi-desktop took alot of fiddling in whatever app was for screen resolution, and also I had to switch to Metacity because having the slidy compiz desktop was causing problems).

ANYWAY: I didn't wipe Vista off however, as I like a spot of Half Life 2 and didn't want to remove it before trying Steam it in WINE incase WINE failed me. To make my life easier, I shrunk down the Vista partition within Vista. Unfortunately, it didn't shrink down much, and after seeing the Ubuntu installer tell me that I could install Ubuntu on space that didn't exist, I didn't fancy trying to see if Vista would survive a shrink from Ubiquity. But the main point is now I want more than 60GB of my 160GB hard drive in Ubuntu.

The question: I can't shrink the Vista partition any more within dear Windows (I checked and defragged about a zillion times), so is it safe to just shrink that from the Live CD and then adjust the space around it?

My HDD layout is:  Some Dell Partition (39MB) | RECOVERY (E) (15GB) | Vista (C) 72GB | SWAP (2.86GB) | Ubuntu (58 GB). 

Would my plan to shrink Vista, then move the swap left, then expand Ubuntu fail miserably? Would I need to reconfigure GRUB? Will Vista shrink any more in GParted if it won't in the Vista Disk Manager? Is it possible without a reinstall?

Wow, first post was long and demanding, sorry guys!

Hope someone can help.
Thanks very much (reading it was a task in itself)!

---

### Post by Skripka on 2009-05-12
I've read (many) disaster stories of trying to shrink Vista partitions from Linux (rather than from Windows).  If Windows won't let it whrink further, I wouldn't push my luck.

---

### Post by oddeyed on 2009-05-13
OK then, I won't go that route, thanks for the quick reply. Do you (or does anyone) have an idea how to make Vista let it shrink further then?
And if I did that, would shifting the spaces make me have to reconfigure GRUB even if I keep them in the same order?

Thanks again,

---

