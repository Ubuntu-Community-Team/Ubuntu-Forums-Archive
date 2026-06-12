---
title: "Kubuntu Installation Problem"
date: 2005-08-17
forum: Desktop Environments
---

### Post by Optiker on 2005-08-17
Deleted previous Mandrake 10 partitions, and booted with Kubuntu install CD in drive. In partition section, chose to use empty space - ie, previous but deleted Mandrake 10 partitions. Total available space is about 17 GB.

Installation launched as expected. Got to the step of "install remaining software" or whatever the terminology is, just before timezone config and it failed to install. I retried, then retried skipping that step, etc. but with no luck continuing. Aborted install and retried it from start.

Got to partition section and it showed the two Linux partitions (Ext3 and swap) but wouldn't install to them. Am trying to be very careful to not damage my 130 GB or so WinXP partitions since they are the meat of my work. I went back and deleted the two Linux partitions that the first Kubuntu try had created and tried again. This time, it didn't seem to recognize space as empty, so I rechecked from Windows XP Disk Manager and it shows that space as available.

Don't know how to proceed from here. Can't seem to get past the partition step, and once I do, then not sure it will get past the "install remaining software" step.

Incidentally, when I deleted the partitions containing Mandrake, the boot loader still comes up with those options. I had planned on modifying it once I got Kubuntu installed. Perhaps that's causing a problem? How do I change that? I know I can get back to the XP boot loader, but not sure I can find my original XP CD since this was a company purchased comnputer with our IT services preinstalling XP.

I am a relative Linux noob...don't do well at command line! The reason I wanted to try Kubuntu ios that I have friends who are less computer literate than I am who want to try Linux, and Kubuntu seems a good disro to try for ease of installation, but with good connections to Debian.

Any help appreciated!
Optiker

---

### Post by guitard00d on 2005-08-17
First of all, if you are worried about damaging any partitions in that computer, your safest and smartest choice would be to temporarily disconnect those drives. If you only have one drive that you intend to split up to host multiple operating systems, back up anything that you can't afford to lose.

But honestly, your best bet is to just install Linux on a separate drive. It would just be safer that way and easier on you since you're not comfortable at a command prompt. There is also a very minimal performance boost by using a separate drive, but it's not humanly noticeable.

As for getting the XP boot loader back. Take a DOS boot disk that has fdisk on it, boot from the disk and then run "fdisk /mbr" and that will restore your XP boot loader.

---

### Post by Optiker on 2005-08-17
Please disregard...made sure partitions were empty, rebooted and tried again...no problem. Installed clean and am using it now.

Nice to know there's a forum available for questions...sure you'll se me again!  :)

Optiker

---

