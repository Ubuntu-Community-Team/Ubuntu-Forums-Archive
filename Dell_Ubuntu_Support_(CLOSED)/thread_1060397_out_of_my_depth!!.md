---
title: "out of my depth!!"
date: 2009-02-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by sailthesea on 2009-02-04
Question  Re: my first day!
Hi Guys
OK I'm a bit lost now I understand I need to manually partition my drive before I install but I not at all sure how to do this safely. Years ago I would simply have reformatted the whole thing from DOS and gone for a fresh OS install but I'd like to try out a dual boot system for a while before I ditch Windows altogether I haven't moved on as much as the technology so am kind of in the dark on this one It would great if anyone has a few pointers for me Cheers!!

---

### Post by bgerlich on 2009-02-04
Just put in the Ubuntu install media and boot from it. The installation program you'll have on your Ubuntu desktop (working from CD) will give you an option to resize the windows partition and will do all the work for you. Just remember to defragment the drive and check it for errors in Windows, you don't have to, just in case.

---

### Post by yther on 2009-02-04
If your laptop came with Vista, as my Inspiron did, I'd recommend you use Vista's built-in tools to shrink your Windows drive.  My preferred procedure would be:

[LIST=1]
[*]Boot into Safe Mode, right-click your disk and hit Properties, then Tools tab
[*]Check disk for errors
[*]Defragment disk
[*]Right-click on My Computer and hit Manage, then from there click on Disk Management under Storage section
[*]Find your Windows volume and right-click it, then select Shrink
[*]Vista should now tell you how much it is possible to shrink the volume.  You may need to run some third-party defragger (like jkdefrag) to collapse everything toward the physical start of the disk, if you have a lot of empty space that Vista won't let you reclaim.
[/LIST]

After that, I'd boot from the Ubuntu CD and proceed with partitioning and installing.  I'd suggest you make at least three slices for Ubuntu: One for OS, one for swap, one for /home where your personal files and settings will go.  That way if you need to erase the OS you won't lose your personal stuff.

Have fun and good luck!  :D

---

### Post by sailthesea on 2009-02-04
Thanks Guys 
  I'm using Windows 2000, don't laugh its an old machine that I inherited, but hardwarewise its pretty good {Dell Latitude C640} but the software isn't up to much and without any CDs I seem to be a bit restricted I know 8.04 will get the best from it but have never come up against this before I'm sure the answer is dead obvious but I'm stuck 
Cheers

---

### Post by yther on 2009-02-04
Ah, well in that case you can still do the first 3 steps I listed.  Windows versions prior to Vista did not provide the ability to resize the working volume, so you'll need to use the Ubuntu tools to do that.  I'd still recommend running [jkdefrag]("http://www.kessels.com/Jkdefrag/") (it's a Windows utility) to squeeze everything together at the start of the space, for maximum ability to shrink the Windows drive.

You may also want to play with a LiveCD before actually installing, so you can tell whether all the hardware is correctly detected.  I had a couple of problems (particularly with wireless) with 8.04 that were fixed in 8.10.

---

### Post by sailthesea on 2009-02-04
Hey Thanks yther
  I think I get it now, I just couldn't figure out how to edit the partition from windows on this machine I'll try your advice out and see how it goes 
Thanks again

---

### Post by armandh on 2009-02-05
dont forget to back up what ever you must save.
some times stuff happens.

---

