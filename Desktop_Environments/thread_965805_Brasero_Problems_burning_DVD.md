---
title: "Brasero: Problems burning DVD"
date: 2008-10-31
forum: Desktop Environments
---

### Post by botfish on 2008-10-31
I am having problems burning DVDs with Brasero Disc Burner.

All appears ok until writing is 99% done then there a long delay then

Error while burning: Unhanded error, aborting.

When I browse the disk is appears to have burnt successfully.

I have the checked the "Increase compatibility with Windows systems" box

Media: imation 16x DVD-R
Brasero version 0.7.1
DVD drive: LG DVDRAM GH20LS10
Ubuntu 8.04 (hardy)
Gnome 2.22.3
Kernel 2.6.24-21-generic

$ cdrecord -version
Cdrecord-yelling-line-to-tell-frontends-to-use-it-like-version 2.01.01a03-dvd 
Wodim 1.1.6
Copyright (C) 2006 Cdrkit suite contributors
Based on works from Joerg Schilling, Copyright (C) 1995-2006, J. Schilling

In the log ther are many lines similar to this:
BraseroGrowisofs stderr: Using 2005_000.JPG;1 for  /2005-12-03_013.jpg (2005-12-04_068.jpg)


Last 27 lines of Brasero session log:
BraseroGrowisofs stderr:  99.33% done, estimate finish Sat Nov  1 13:37:08 2008
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: Total translation table size: 0
BraseroGrowisofs stderr: Total rockridge attributes bytes: 11324
BraseroGrowisofs stderr: Total directory bytes: 0
BraseroGrowisofs stderr: Path table size(bytes): 10
BraseroGrowisofs stderr: Done with: The File(s)                             Block(s)    216274
BraseroGrowisofs stderr: Writing:   Ending Padblock                         Start Block 216317
BraseroGrowisofs stderr: Done with: Ending Padblock                         Block(s)    150
BraseroGrowisofs stderr: Max brk space used 21000
BraseroGrowisofs stderr: 216467 extents written (422 MB)
BraseroGrowisofs stderr: :-[ WRITE@LBA=34d90h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs called brasero_job_set_progress
BraseroGrowisofs called brasero_job_set_current_action
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2270)

---

### Post by Cammy on 2008-11-01
I know this isn't the answer you're looking for, but maybe you can file it in the back of your head in case you can't get your problem solved.

I too had numerous problems with Brasero, and after trying several things, I finally took someone's advice and installed k3b.  I've never had a problem burning anything with it.

May you have better luck fixing your Brasero problem than I did.

---

### Post by LDRoamer on 2008-11-01
I have had the same problem with Barsero. I am going to try K3b and see if that helps.

---

### Post by botfish on 2008-11-04
I installed K3b and it's working well.

Thanks for your advice.

---

### Post by LDRoamer on 2008-11-04
K3b is not working for me. It goes through the process fine and gives no errors but the disks cannot be read in windows. They work fine in Ubuntu but windows sees them as empty.

---

### Post by theduffman on 2008-11-05
> **LDRoamer said:**
> K3b is not working for me. It goes through the process fine and gives no errors but the disks cannot be read in windows. They work fine in Ubuntu but windows sees them as empty.

what filesystem setting did you choose for it, Linux or Linux+windows(Joliet)

---

### Post by LDRoamer on 2008-11-08
How do I select a file system setting? I can't seem to find anything in K3b that refers to that.

---

### Post by LDRoamer on 2008-11-08
Okay I did find the setting and it was set to linux and Windows. This doesn't help as the disk is still not readable in windows.

> **LDRoamer said:**
> How do I select a file system setting? I can't seem to find anything in K3b that refers to that.

---

### Post by theduffman on 2008-11-08
> **LDRoamer said:**
> Okay I did find the setting and it was set to linux and Windows. This doesn't help as the disk is still not readable in windows.

thats odd. try a UDF setting.
should work tho with Joliet.  is it finalised?

---

### Post by alwayshere on 2008-11-08
you could try using k9copy to make an iso file then just right click on iso file and choose write to disk

---

### Post by alwayshere on 2008-11-08
follow this to update your iso stuff 

In terminal

sudo apt-get install genisoimage

push enter

sudo apt-get update

push enter

sudo apt-get install wodim

push enter

sudo apt-get update

push enter

---

### Post by gsxrmike04 on 2008-11-13
wow thanks that worked great !

---

