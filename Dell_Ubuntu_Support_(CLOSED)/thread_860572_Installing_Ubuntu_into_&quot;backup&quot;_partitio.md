---
title: "Installing Ubuntu into &quot;backup&quot; partition of dell"
date: 2008-07-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Warthaug on 2008-07-15
I have a dell XPS M1330 laptop which came with vista.  I've been running ubuntu on an external hard drive for a while, and want to install it onto my laptop as a separate partition - in fact, my laptop has a 10gig "recovery" partition that I was planning on using.  I was going through the install process and came across a few things that gave me pause, namely:

The ubuntu partitioner lists a series of partitions; the main drive (C:, about 120 gigs), the recovery drive (D:, about 10 gigs) and two other partitions, one ~33megabytes in size, one ~2 gigs in size.  The later two are not normally visible as drives in windows, but  appear as partitions on both the ubuntu and windows partitioning programs.

I tried to proceed instillation, using the recovery partition as the source.  I could delete the old partition, but couldn't split it into two (I could make one partition, but the remainder was "unusable").

This brings up a few questions:
1) Would it be better to use the windows partitioner to make the recovery partition empty space, and then use that for install?

2) What are the two "hidden" partitions, and can I use them for my ubuntu install without screwing up my laptop?

3) Is their a step-by-step guide for what I want to do?  None of the ones I've found deal with the "issue" of having multiple pre-existing partitions, one of which (or two or three) you want to use for ubuntu.

thanx

Bryan

---

### Post by PinkFloyd102489 on 2008-07-16
The first hidden is the EISA configuration at the front of the drive, which I dont recommend messing with. The second hidden, which is at the end, is Dell's MediaDirect program. It allows you to boot into MediaDirect to watch movies, etc without booting into the actual OS.

I personally got rid of it and set the Home button to boot into Ubuntu and the power button to boot into Vista.

---

### Post by Warthaug on 2008-07-16
Hmmm, get rid of media center.  How nice that would be!

So one last question - how to I re-map the button so that ubuntu loads instead of media center?

Thanx!!!!

Bryan

---

### Post by allenbradley on 2008-07-17
this might come in handy :
[http://forum.notebookreview.com/showthread.php?t=231747](http://forum.notebookreview.com/showthread.php?t=231747)
tough this is the opposite of what PinkFloyd102489 suggested (ie) mediadirect boots into vista/xp and power into ubuntu.

---

### Post by PinkFloyd102489 on 2008-07-17
Im pretty sure you can swap the instructions if you want.

---

### Post by allenbradley on 2008-07-18
PinkFloyd102489, could you please tell how you swapped keys? Did you use the rmbr in mediadirect or by some other method?

---

### Post by TimDaniels on 2008-07-21
I advise that you clone your Vista to your external drive and then delete all the partitions on the internal drive.  The utility partition is redundant because they are on the utility CD that comes with the laptop.  The System Recovery partition is worthless after a couple weeks of ownership because it wipes out every setting and piece of data and installed app that you added to the system.  The MediaDirect partition is a POS that will only have you swearing at Dell and then at yourself if you try to diddle with it - such as adding one or more logical drives to accomodate Linux.  You can run "rmbr DELL x y" from the DellKit folder of the MediaDirect recovery CD on the command prompt terminal of the Vista Repair facility, but you will be toying with system death.  The best thing to do is to make a Gparted live USB (see the Gparted website) to remake the partitions since Vista has its own partitioning scheme, now, that no other utility in the world uses, and mixing the Vista-created partitions with other partition editors can lead to "disappearing partitions".  (But Vista understands the pre-Vista partitioning, so Gparted works well as the universal partition editor.)  Then re-clone Vista into the 1st partition and then run "bootrec /rebuildbcd" to fix up the BCD menu.  If you use Casper to do the cloning (or other such cloner), you can shrink Vista down to fit in a 20GB partition on the external drive.  Then you can expand it back up to any size you want when you re-clone it to the laptop's internal drive.  You don't have to do any formatting of any partition as the formatting is part of the clone, and the Ubuntu (Linux) installer wants to do the formatting so that it can install the boot sector for Ubuntu as well.

BTW, is your external drive a USB drive?  I've found that I cannot boot Vista or Ubuntu using an eSATA external drive connected to a PCIe eSATA adapter card.  I'm now considering using an external USB drive for that.

*TimDaniels*

---

### Post by TimDaniels on 2008-07-21
I didn't make clear that I recommend ****-canning MediaDirect.  It just gums up any re-partitioning that you want to do, and it's already installed as an app in Vista, anyway.  If you clone and then re-clone Vista, you won't lose it, and you can do away with the MediaDirect partition.  Just run "bootrec /fixmbr" and "bootrec /fixboot" to restore the standard Microsoft items.  On my M1330, pressing the "house" button just brings up the MediaDirect splash screen.  That's all.

*TimDaniels*

---

### Post by allenbradley on 2008-07-21
> **TimDaniels said:**
> You can run "rmbr DELL x y" from the DellKit folder of the MediaDirect recovery CD on the command prompt terminal of the Vista Repair facility, but you will be toying with system death.

what exactly happens when you do that?

---

### Post by jost1989 on 2008-07-21
> **PinkFloyd102489 said:**
> 

I personally got rid of it and set the Home button to boot into Ubuntu and the power button to boot into Vista.


How did you set it up to do that? I would LOVE that on my laptop...

---

### Post by TimDaniels on 2008-07-23
> **allenbradley said:**
> what exactly happens when you do that?

For one thing, when you press the power button, it sets the "x" partition "active".  When you press the house button, it sets the "y" partition "active".  That makes the MBR pass control to one partition or the other.  But it also screws around with other unknown things.  Take the name "rmbr" for instance.  Is that an acronym for "replace MBR"?  Who knows?  Another thing is that the MediaDirect partition is the last partition on the drive, and it is a logical partition of type code D7(hex), IIRC.  How significant is each of those features?  Who knows?  All I know is that after weeks of screwing around with MediaDirect and rmbr, I got fed up with restoring things using multiple live CDs, installation CDs, clones, and a live USB.  I figure now that getting separate buttons for each OS is just not going to impress anyone appreciably, much less oneself - especially if you intend to boot multiple installations of Linux (as I do).  Do a Google search on "rmbr MediaDirect" and you'll find one or two successes with cute uses for the house button, and even then, later posts by the "succeeders" point out subsequent corruptions.  If rmbr were thoroughly documented, it could be used with confidence, but...

*TimDaniels*

---

