---
title: "HD Deleted"
date: 2010-10-26
forum: Desktop Environments
---

### Post by joeyarnold on 2010-10-26
Anyways, some bad news.
 
My computer broke last Saturday, Oct. 23rd 2010.
I'm trying to fix it.
 
I have two 80 GB HDs on my desktop PC (Personal Computer).
(HD: Hard Drive: the brains of computers, the memories, the data, everything almost)
(desktops are towers, big sometimes, not laptops)
 
One of them use to be an external HD.
The first HD had Linux's Ubuntu OS.
(OS: Operating System: free compared to Apple & Microsoft).
 
& the second HD was the slave.
The second HD had about 60 GB worth of my videos, pictures, files.
 
But the first HD one had Ubuntu like I said already.
It was Ubuntu 10.10 with the latest updates.
 
But then my computer was slow. Many problems.
I Would turn it off sometimes the wrong way. Would just press the off button.
 
Then it wouldn't boot.
It goes to this BusyBox
Which is a type of terminal or MS-Dos or shell or program.
They tell you to wait so that it will fix itself.
 
But several hours later, nothing happened.
Tried restoring. Nothing. I kept restarting it, fixing it, reconfiguring, restoring.
 
.
 
But then reinstalled Ubuntu from CD.
(Ubuntu is now working again, but that's not the problem).
 
But I ended up doing manual configuration.
To my second slave HD during re-installation.
 
I went to first partition in set up.
It was suppose to partition, grab some free space for Ubuntu.
 
I went to just make several partitions.
For Ubuntu to work on this second slave HD.
 
But as soon as I went to resize partition.
Then it reconfigures what was on that second slave HD.
It originally told me I had 60 GBs of used data on this 2nd HD.
 
It split the partition.
I was trying to split it & put Ubuntu in a free partition.
 
That worked.
But then the original partition.
That was storing all of my stuff was no longer using 60GBs.
 
It went down to like 4 GB or something.
Maybe less.
 
.
 
In other words.
 
I may have deleted my second HD.
I'm looking at trying to restore what I deleted.
Either it was deleted or it is hidden.
 
I have heard that things never totally get deleted off HDs.
 
If that is true then there has to be a way.
 
Either it was destroyed.
(which then means that it's possible to actual terminate data off HDs)
(which is good if you want stuff totally deleted)
(like if you needed to rid yourself from top secret FBI work)
(or you want to destroy a love letter that you want nobody to see)
 
Anyways, either my stuff is gone.
Or it was just misplaced, renamed, stuck in the root, the secret PC parts.
 
I think I'm going to repost this to forums.
 
I will not rest until I figure this thing out.
 
 
Joey Arnold
503.367.4695&#65279;

---

### Post by theDaveTheRave on 2010-11-04
Joey,

open a terminal and try the following.

```

ls /dev/disk/by-id
```

each disk can have multiple ID's, so read the output carefully, look particularly at the 'part... ' section at the end of each line - this is the partition number.

then check to see what is mounted and where.

```

df

```

will show you what the usage of the disks are, and if you have subpartitions on a disk they appear underneath the main part.

You will need to compare the outputs to see whats going on.

once you have 'located' your missing disk, you should be able to mount it somewhere, and then check to see if you really have lost the data.

Proviso.

If you have somehow overwritten the file table info on the disk, then you may find that the files are gone. However under normal cirumstances I wouldn't expect the system to overwrite stuff unless you where performing a complete re-format.

hope this info helps

David

---

### Post by azertyh on 2010-11-04
hello,

some docs to recover data :
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by joeyarnold on 2010-11-12
@ [theDaveTheRave]("http://ubuntuforums.org/member.php?u=246735"): 
Thanks, I tried "ls" in terminal & here are the results below. 
I will have to think about all of this some more now.

ls /dev/disk/by-id 

ojawall@ojawall-desktop:~$ sudo ls /dev/disk/by-id
[sudo] password for ojawall: 
ata-WDC_WD400BB-00CJA1_WD-WMAAE1345795
ata-WDC_WD400BB-00CJA1_WD-WMAAE1345795-part1
ata-WDC_WD400BB-00CJA1_WD-WMAAE1345795-part2
ata-WDC_WD400BB-00CJA1_WD-WMAAE1345795-part5
ata-WDC_WD800BB-75FRA0_WD-WMAJD2235285
ata-WDC_WD800BB-75FRA0_WD-WMAJD2235285-part1
scsi-SATA_WDC_WD400BB-00CWD-WMAAE1345795
scsi-SATA_WDC_WD400BB-00CWD-WMAAE1345795-part1
scsi-SATA_WDC_WD400BB-00CWD-WMAAE1345795-part2
scsi-SATA_WDC_WD400BB-00CWD-WMAAE1345795-part5
scsi-SATA_WDC_WD800BB-75FWD-WMAJD2235285
scsi-SATA_WDC_WD800BB-75FWD-WMAJD2235285-part1
ojawall@ojawall-desktop:~$ ^C
ojawall@ojawall-desktop:~$

---

### Post by joeyarnold on 2010-11-12
@ [theDaveTheRave]("http://ubuntuforums.org/member.php?u=246735"): I typed df into the terminal.

df

ojawall@ojawall-desktop:~$ sudo df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1             37002824   4572948  30550224  14% /
none                    250260       356    249904   1% /dev
none                    254480       196    254284   1% /dev/shm
none                    254480       192    254288   1% /var/run
none                    254480         0    254480   0% /var/lock
none                    254480         0    254480   0% /lib/init/rw
ojawall@ojawall-desktop:~$

---

### Post by joeyarnold on 2010-11-12
@ azertyh: thank you for the hookup. Unfortunately, I already ran into these sites before & tried all their advice already. But I may just try them again. I will try posting my progress.

Data Recovery Tips
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

TestDisk How-To
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by joeyarnold on 2010-11-12
sudo parted /dev/sda

ojawall@ojawall-desktop:~$ sudo parted /dev/sda
GNU Parted 2.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted)

---

### Post by mbuell on 2010-11-12
> **joeyarnold said:**
> . . .
 
I may have deleted my second HD.
I'm looking at trying to restore what I deleted.
Either it was deleted or it is hidden.
 
I have heard that things never totally get deleted off HDs.
 
If that is true then there has to be a way.
 
Either it was destroyed.
(which then means that it's possible to actual terminate data off HDs)
(which is good if you want stuff totally deleted)
(like if you needed to rid yourself from top secret FBI work)
(or you want to destroy a love letter that you want nobody to see)
 
Anyways, either my stuff is gone.
Or it was just misplaced, renamed, stuck in the root, the secret PC parts.
 
I think I'm going to repost this to forums.
 
I will not rest until I figure this thing out.
 
 
Joey Arnold
503.367.4695&#65279;

Joey;

I'm going to give you some generalities, to help you understand where you are. I see that others are chipping in with specific techniques to help you find out where you are, and this is good. 

First - True or False: NOTHING is ever lost from a hard drive. False. While there is a lot that remains on a hard drive after you think you have deleted it, it DOES and WILL eventually be lost forever. There are a number of steps that you can make to insure that this does happen (i.e. LOSE the data). Changing the partition table, which sounds like what you did, is right at the top of the list. If you actually messed up the partition the data was on, it would take an EXPERT to restore any of the data that was there - along with specialized software - and it would not be cheap. It is also not as complete as the news people would have you think (they do like their drama). Restoring lost data is not an ordinary skill. 

Since we are advising you without being able to see what you see, this is a problem. Every time you are using this computer with the hard drive hooked up you could be erasing more of your data. I would advise you to run, not walk, to the nearest super-techie computer guy you know, and bribe him with whatever it takes to help you. 

You are in uncharted waters for you, and you would be safer with a good pilot. 

Good luck.

---

