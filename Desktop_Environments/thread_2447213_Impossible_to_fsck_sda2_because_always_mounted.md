---
title: "Impossible to fsck sda2 because always mounted"
date: 2020-07-15
forum: Desktop Environments
---

### Post by cdnhermit on 2020-07-15
This morning I had problems to the point  that i could not log in in **Ubuntu 18.04**. For a couple of weeks, on start up, I had error messages numbers, i guess, blocks of info. And this morning I noticed: inode count wrong, check count wrong. So I reinstalled Ubuntu 18.04 this afternoon because I could not run **fsck** in recovery mode. It was impossible to unmount **/dev/sda2**.
I reformatted that partition and reinstalled. Now, I still have the same problems, with error messages before the magenta screen and I still can not run **fsck** on the recovery because it is still mounted.
I am not so sure that it reformatted the partition on my ssd because i have the same errors and the same problem. Someone has a solution for me to unmount this this partition so that i can run **fsck**?
Thank you

---

### Post by CatKiller on 2020-07-15
If you are having errors even after reinstalling, that seems like hardware failing to me.

For being able to run fsck without mounting the partition that holds fsck, there are two approaches. The first is to run fsck before the partition is mounted; that happens automatically from time to time, or can be triggered to happen at the next boot. The other is to boot up the installer (or other live environment) and run the fsck from there rather than the one on the partition that you want to check.

---

### Post by cdnhermit on 2020-07-15
Thank you for your suggestion. I am not very tech, so I would not know how to proceed for your two suggestions.
1) How can I do "run fsck before the partition is mounted",  I don't see how I can do that;
2) I do not know how I could do this one: "to boot up the installer (or other live environment)", could you explain?

Currently I have a pc with windows10 and I have an external ssd on which I installed Ubuntu. On power on, after many seconds (bios) it goes to the magenta screen to choose Ubuntu, Win or recovery. I also have Ubuntu on a usb flashdrive.
Thank you

---

### Post by CatKiller on 2020-07-15
If it's an external drive then it could be cabling or similar causing you problems rather than the drive itself. > **cdnhermit said:**
> 1) How can I do "run fsck before the partition is mounted",  I don't see how I can do that; 

I mentioned it mostly to say that it happens automatically every certain number of times that the drive is booted. You used to be able to trigger it on the next boot by creating an empty file in the root directory called *forcefsck*, but I don't know if that method works any more. 

>  2) I do not know how I could do this one: "to boot up the installer (or other live environment)", could you explain? 

The thumb drive or DVD that you install Ubuntu from is a complete and functional Linux environment, with all the usual tools. In particular, that means that you have access to fsck in addition to the one that's on the partition that you want to check. You'd just boot up from that as you did when you installed Ubuntu, but you'd chose to "try Ubuntu" rather than "install Ubuntu." Then open a Terminal and run your filesystem checks with ```
sudo fsck /dev/sda2
``` (be aware that the drive device identifier - the sda part - can change from boot to boot, particularly if you have some other device plugged in) 

The installer is what you probably already have - in fact, you say "I also have Ubuntu on a usb flash drive" - so that's the one to go with, since you already have it, but projects make live images available for all sorts of things and any of them would let you do this. Whatever you have to hand. Booting into a live environment is a very useful troubleshooting technique in general for repairing things more easily.

---

### Post by TheFu on 2020-07-15
There are 3 ways to fsck file systems that are mounted and required on a running Linux system.
[LIST]
[*]There is a grub command line to do it.  I know this exists, not the exact command. Sorry. You'd enter this using the grub boot editor - press 'e' when the grub boot menu is shown.
[*]Go into "rescue mode" - 
[LIST=1]
[*]from the grub boot menu, there should be "**Advanced Options**" - choose that and 
[*]Select **rescue**/failsafe ... or something like that.  Don't worry if there are a few different kernel versions listed. Pick the first one. If that fails, try the 2nd or 3rd until one works.
[*]That will display a TUI - text-based GUI.  In the list shown, there will be "**FSCK all file systems**" - choose that.
[/LIST]
[*]Use a "Try Ubuntu" boot disk/flash drive/whatever.  For fsck, just having the same release is sufficient, it doesn't need to be the exact same DE/GUI.  I routinely use an Ubuntu-Mate "try ubuntu" flash drive when I need to fsck Ubuntu Server systems.  As long as they run the same base release (both 20.04, both 18.04, or both 16.04), then that is sufficient.
[/LIST]

Before systemd took over mounting file systems, getting the fsck at boot was really easy. **sudo touch /forcefsck** and reboot.  The mount process looked for that file and if it existed, it would run an fsck then remove the file. Simple, effective.  Before systemd-mount decided to "improve" stuff.  So, if you find yourself searching for exact directions and they say to create a file "forcefsck", those instructions are out of data on systemd controlled systems.

Oh, if the install uses advanced volume management or encryption, it may be necessary to use the "Try Ubuntu" method and manually unlock and open all the volumes. Sorry, I don't recall whether Rescue mode will handle that stuff correctly or not.

---

### Post by cdnhermit on 2020-07-15
Thank you CatKiller for your explanations. I put the flash drive in my pc and opened a terminal and here is the result:

ubuntu@ubuntu:~$ sudo umount /dev/sda2
ubuntu@ubuntu:~$ sudo fsck -y /dev/sda2
fsck from util-linux 2.31.1
e2fsck 1.44.1 (24-Mar-2018)
/dev/sda2: clean, 300312/3203072 files, 3978149/12800000 blocks
ubuntu@ubuntu:~$ 

That does not say much, to me anyway! Why did I get that problem? That will be great the day we have explanation for all problems! hihihi.

I tried the following but it does not work.
ubuntu@ubuntu:~$ sudo fsck -A -r -y /dev/sda2
fsck from util-linux 2.31.1
ubuntu@ubuntu:~$ sudo fsck -A -y /dev/sda2
fsck from util-linux 2.31.1
ubuntu@ubuntu:~$ sudo fsck -A  /dev/sda2
fsck from util-linux 2.31.1
ubuntu@ubuntu:~$

---

### Post by CatKiller on 2020-07-15
> **cdnhermit said:**
> Why did I get that problem? 

You haven't said what your error messages were, so there's no way to even guess. Having fsck messages during the boot process isn't necessarily related, since fsck gets run automatically every n boots anyway.

---

### Post by TheFu on 2020-07-16
Someone jumped into fsck. Seems an assumption was made about the file system being corrupt.  This may have been true.  Because help was asked for concerning fsck, that is what was provided.

If it were in my system, I'd have done a few data gathering things ASAP.
Run:
[LIST]
[*]```
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
[*]```
sudo fdisk -l
```
[*]Determine the actual file system type and mount location.  Device names like sda can change. When a USB flash drive is booted, often it will become sda and all the other devices will be shifted/moved around. Every boot, we have to check to ensure we are working with the correct device and partition number.
[*]Manually mount the file system ... which may not actually be on sda2. There are other "containers" which hold file systems. If that mount fails - there would be an error.  **journalctl** will access errors in the system logs if requested. I'd check those.  For example:
```
journalctl -p err
....
Jul 12 20:44:43 romulus smartd[1674]: Device: /dev/sdc [SAT], 2 Currently unreadable (pending) sectors
Jul 12 21:14:43 romulus smartd[1674]: Device: /dev/sdc [SAT], 2 Currently unreadable (pending) sectors
Jul 12 21:44:43 romulus smartd[1674]: Device: /dev/sdc [SAT], 2 Currently unreadable (pending) sectors
...
```
[/LIST]Check the system logs and look up each problem.
The error from the mount attempt should be pretty clear that the file system has corruption.

Regardless, I'd run a short SMART test .... **sudo smartctl -t short /dev/sda**  # or sdb or sdc or sdd or sdf or ..... SMART is for an entire disk, not a partition.  Then wait at least the prescribed period.  To see the test results, **sudo smartctl -a /dev/sda**  probably want to redirect those to a file and pager for review.  Lots of threads here with smart data output that highlight the results.  Really is good to check these things at least monthly for all your storage devices ... except SDHC and USB false stuff.  SSD and HDD all support SMART.  A failing disk should jump out, but about 22% of the time, no SMART data issues are shown.  That's why we need backups.

---

