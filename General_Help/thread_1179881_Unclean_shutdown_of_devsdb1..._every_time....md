---
title: "Unclean shutdown of /dev/sdb1... every time..."
date: 2009-06-06
forum: General Help
---

### Post by t0p on 2009-06-06
I installed Jaunty NBR to my Eee PC 701.  I installed / to the SSD and /home to a 4 GB SD card that I keep permanently in the SD card slot.  I formatted the SSD and the SD card to ext2, as I believe it's better than ext3 for flash drives (less writing to disk).

Problem is, every time I boot the Eee I get a message that /dev/sdb1 (the SD card) was shut down uncleanly, and the disk has to be checked for errors before Ubuntu can boot.

What's up with this?  Is Ubuntu failing to automatically unmount the SD card when I shut down the computer?  No faults have been found on /dev/sdb1 yet.  But isn't there a risk that some faults may develop if the card continues to be shut down uncleanly?

---

### Post by howardf42 on 2009-06-21
I have exactly the same issue.  I've had this problem also with eeebuntu which I had installed before Ubuntu NBR.  Today fsck started on bootup and discovered several errors which were fixed with a manual fsck run.  Still haven't been able to find a solution.  Keep me posted if you find something.

---

### Post by Roasted on 2009-06-24
Sorry if you got your hopes up seeing a response to your thread, but I'm just here to confirm you aren't alone.

I'm running Ubuntu 9.04 64 bit on my computer. For a while I would boot up and get really inconsistent boot issues. Sometimes I got error 16, other times error 18. I also saw error 22 once or twice as well. Rebooting several times would normally help and I could eventually boot. This time around, didn't work. I did a fsck and I still get the unclean shutdown garbage. 

I'm considering reinstalling Ubuntu. But that's the way I fix Windows installs. I don't want my Windows habits to turn into an Ubuntu habit. I'm trying to figure out how to get it fixed...

Hopefully we find some answers... soon!

---

### Post by dcstar on 2009-06-24
> **t0p said:**
> 
........
What's up with this?  Is Ubuntu failing to automatically unmount the SD card when I shut down the computer?  No faults have been found on /dev/sdb1 yet.  But isn't there a risk that some faults may develop if the card continues to be shut down uncleanly?

It is possible that the SD card part of the kernel is being closed before the /home unmount has concluded. It is not beyond comprehension that the kernel developers did not anticipate something like this sort of removable hardware being used in this manner.

Things like this should be reported using the usual bug report system, this is the only was these will ever get properly addressed (complaining in a forum like this will do little to resolve such issues).

---

### Post by howardf42 on 2009-06-24
> **dcstar said:**
> It is possible that the SD card part of the kernel is being closed before the /home unmount has concluded. It is not beyond comprehension that the kernel developers did not anticipate something like this sort of removable hardware being used in this manner.

Things like this should be reported using the usual bug report system, this is the only was these will ever get properly addressed (complaining in a forum like this will do little to resolve such issues).
Good suggestion.  The following bug report has been posted"

**[SIZE=2][Bug 391717] [NEW] Unclean shutdown of /dev/sdb1... every time...[/SIZE]**


Stay tuned.

---

### Post by Mighty_Joe on 2009-06-24
I have a similar problem running Ubuntu from a USB flash drive.  Every boot I get the same message that the drive was "not cleanly unmounted".
I did some digging in Launchpad a while ago and found [this bug]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/125702").  It sounds like there's some problems in the shutdown scripts.

---

### Post by howardf42 on 2009-07-07
> **howardf42 said:**
> Good suggestion.  The following bug report has been posted"

**[SIZE=2][Bug 391717] [NEW] Unclean shutdown of /dev/sdb1... every time...[/SIZE]**


Stay tuned.
If you are experiencing the same problem, it would be helpful if you chime in on the bug report and let them know that you also experiencing this.

[https://bugs.launchpad.net/ubuntu/+bug/391717](https://bugs.launchpad.net/ubuntu/+bug/391717)

Thanks,
Howard

---

### Post by t0p on 2009-07-10
> **howardf42 said:**
> If you are experiencing the same problem, it would be helpful if you chime in on the bug report and let them know that you also experiencing this.

I shall do so now.

---

### Post by pjalegria on 2010-05-22
Same problem... Lucid UNR with home on SD card

---

### Post by Mighty_Joe on 2010-07-08
> **pjalegria said:**
> Same problem... Lucid UNR with home on SD card

This is a blast from the past. . .
I switched to ext3 for my flash drive install and the problem went away.

---

