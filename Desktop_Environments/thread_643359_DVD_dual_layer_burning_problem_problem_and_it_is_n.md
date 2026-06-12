---
title: "DVD dual layer burning problem problem and it is not the drive"
date: 2007-12-17
forum: Desktop Environments
---

### Post by ja4509 on 2007-12-17
I have two different drives one internal the other is USB external. Booted up in Ubuntu I cannot burn a Dual layer DVD without creating a coaster. I have tried K3B, Brassero, and Nautilus to burn DVDs. All of these work flawlessly until I try to burn dual layer media. Both drives work fine in windows. All apps work until I do a dual layer burn. K9copy works for DVD9 to DVD5. I create a 7GIG ISO file with K3B and mount it and it is fine. But when I burn it it gets half way through the burn and pukes. With Brassero burning the ISO file it gets about a quarter of the way through and pukes.

Both drives have yes set in the device manager for DVD 9 on both +R and -R. 

At least Brassero gives me some meaningful error output which I will paste below. I am not familiar with growiso or what might be happening but I suspect it is the culprit as all apps seem to depend on it.
---
process (BraseroGrowisofs) stdout:  1176043520/6915010560 (17.0%) @8.0x, remaining 15:22 RBU  99.9% UBU  51.0%
growisofs (BraseroGrowisofs) set_written
growisofs (BraseroGrowisofs) set_total
growisofs (BraseroGrowisofs) set_rate
growisofs (BraseroGrowisofs) set_action
growisofs (BraseroGrowisofs) start_progress
process (BraseroGrowisofs) stderr: :-[ WRITE@LBA=8df40h failed with SK=3h/ASC=0Ch/ACQ=00h]: Input/output error
process (BraseroGrowisofs) stderr: :-( write failed: Input/output error
job (BraseroGrowisofs) asked to stop
	status	= 1
	error		= 1
	message	= "Unhandled error, aborting"
iter (BraseroGrowisofs) stopping
process (BraseroGrowisofs) got killed
iter (BraseroGrowisofs) stopped
job (BraseroGrowisofs) got out of loop
job (BraseroGrowisofs) set_task
Session error : Unhandled error, aborting
--- 

This is just the tail of the file.

Can anybody HELP?

---

### Post by ja4509 on 2007-12-18
After some considerable research I found that growisofs will correctly set burn speed on all media but DVD9. At least on the two different drives when I have auto is selected in the K3B application.

For some reason on auto 8x is set for the burn speed which works great on DVD5 media however it creates a coaster with DVD9 media.

What puzzles me still is that the drive seems to hold back the speed to 4x (the drive's rated speed for DVD9) until it burns somewhere around 25% of the disk then according to the log it all of a sudden pops up to the 8x and bombs out. Granted the drive is reported at 8x when the burn first starts as the "Current Write Speed" but what I can't figure out is why it burns at 4x which the drive is rated for on DVD9 then all of a sudden pops up to 8x. This happens on both drives from two different manufacturers. Yeah, I know even though they are different manufacturers they can both be using the same chip sets and this is one possible explanation. 

And I suspect there is some kind of reset being sent to the drive while the burn is in progress that cause it to use the requested 8x instead of the 4x it was writing at.

Below is an excerpt from the log:
---
DVD+R Dual Layer

Used versions
-----------------------
growisofs: 7.0

growisofs
-----------------------
Executing 'builtin_dd if=/dev/fd/0 of=/dev/sr0 obs=32k seek=0'
/dev/sr0: splitting layers at 1688240 blocks
/dev/sr0: "Current Write Speed" is 8.2x1352KBps.
   24903680/6915010560 ( 0.4%) @3.7x, remaining 27:40 RBU 100.0% UBU   2.0%
---

Well at least I can burn DVD9s now but in Nautilus there is no speed setting so DVD9s are not going to burn correctly in Nautilus. If any body knows of a config file for burn options for Nautilus please post the info.

---

### Post by Dixon Bainbridge on 2007-12-19
I had this problem about a year ago and it was unresolved. Not much help I know, but I know what you mean. My new DVD burner wont burn at all at 4x in ubuntu - does it windows. Very annoying because iso's and audio needs to be burnt at 4x maximum and I can't seem to force it back from 8x.

Help.

---

