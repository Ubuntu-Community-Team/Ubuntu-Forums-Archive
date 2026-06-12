---
title: "Hard drive status inaccessable"
date: 2005-12-21
forum: Desktop Environments
---

### Post by tink445 on 2005-12-21
Hi everyone,

This is my first post to a forum because I have always been able to find an answer for any linux problem by searching various forums and goolge (this one has defeated all my attempts).  I have been using various (mainly Suse 9.1 and Fedora Core 3 + 4, and some others) distros for about 2 years now.


Here's my problem:

I have a file server based on ubuntu 5.10 (recently installed), I used to have Fedora Core 4 on it, but had many problems with it.  I decided to install ubuntu breezy and see if I could have a more stable system (since I use that as a workstation and it is the most stable distro I have used to date).  I installed Ubuntu onto a different HD (not the one that had Fedora on it, just in case somthing like this happend).  I have 7 HD's total in my fileserver (one for the OS and 6 for file storage, all various brands and capacity).  The drive in question is a WD1200JB attached to a PROMISE ULTRA133 TX2 PCI IDE Controller Card.  After I installed breezy without any problems everything booted up fine and all my drives except /dev/hde (hde1) mounted ok.  I checked the System > Administration > Disks Manager, it showed that my drive was detected correctly.  Then under the partitions tab was the following:

device: /dev/hde1
Filesystem: Extended 3
Access Path: /home/matt/storage
Status: inaccessible

When I click on the enable button next to inaccessible it does nothing.

In /etc/fstab I have the following:
/dev/hde1      /home/matt/storage     ext3 defaults 0 0

When I execute: 
```
sudo mount -a
mount: /dev/hdc1 already mounted or /home/matt/mirror busy
```

No matter what I changed I always received the above error.  All my other drive mounted fine with the same fstab entry with the /dev/hd# and mount point changed of course.  I tried a few other things I can't really remember, but eventually I replaced the boot drive with my old Fedora OS on it and booted up.  Fedora correctly recognised my drive, mounted it, and all my data was there and I could access all files fine.  So to me this showed that the drive was NOT corrupted.  After that I put the WD1200JB drive into my workstation (that I'm posting from) as master on the secondary channel and the same thing is happening:

System > Administration > Disks Manager:
device: /dev/hdc1
Filesystem: Extended 3
Access Path: /home/matt/test
Status: inaccessible

On my workstation computer I did about all the same tests as I did on the fileserver, with the same results.  I do not want to format the drive because it has some data that I haven't backed up (It's not real important, but this has become more of a learning quest than anything else). Now when I try to boot from the fedora disk, it freezes when it is checking disks, so I can't back up my data that way.  


```
matt@bt:~$ sudo fsck /dev/hdc1

fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
/test: clean, 44355/14663680 files, 25529300/29296496 blocks
```

Something else to mention, all the drives that mounted correctly on my fileserver had "99" as owner and group, where the drive in question had root for the owner. Changing the owner and group had no effect. Changing permissions on the mount point also had no effect.

Can anyone point in the right direction? Is this a permissions issues?



Fileserver specs:
Asus p4p800e-deluxe Motherboard
Corsair ValueSelect RAM 2x512MB
PNY 6600GT 128MB
Northwood 3.0GHz
PROMISE ULTRA133 TX2 PCI IDE Controller Card

Thanks

Tink445

---

### Post by tink445 on 2005-12-21
Update:

Reading another thread I tried:
```
matt@bt:~$ sudo parted /dev/hdc1

(parted) print
Disk geometry for /dev/hdc1: 0.000-114439.561 megabytes
Disk label type: loop
Minor    Start       End     Filesystem  Flags
1          0.000 114439.561  ext3

(parted) check 1
Error: Filesystem has incompatible feature enabled
```

Maybe this will help someone figure out my problem.

---

### Post by tink445 on 2005-12-29
Problem FIXED!!!

Finally got access to the drive, here's how:

This idea popped into my head today.  I had an IDE to USB 2.0 converter that I use for work sometimes.  I plugged the drive in question with this device into a Fedora Core 4 machine.  Then I went to Applications > System tools > Disk Management.  It showed a new device of /dev/sda, it said: 
device /dev/sda1
start = 1
end = 14589
size = 114440MB
Type = ext3

Next i tried to mount it with all sorts of command variations (usually returned something like wrong fs type, bad option, or bad superblock).  fsck returned bad superblock type errors.  Tried many other things left out for shortness.  

Then I hooked it up to my Breezy computer and  checked System > Administration >Disks.  It took about a minute and then it showed up in the list as:
/dev/sda1
filesystem = extended 3
access path = none (i think)
status = inaccessible.  

Basically the same as before when I hooked it up to the IDE channel except for the /dev/#.  I clicked enable and nothing happend, oops need an access path.  Typed /home/matt/120 (created earlier), clicked enable and up pops my filesystem just where I left it about 3 weeks ago.  As we speak I am copying data off and I am going to reformat it in my fileserver from Ubuntu Breezy.  

**Thanks** everybody for looking at my post, even though no responses.  Maybe somebody can shed some light on why these problems came about and how to prevent something like this in the future.

---

### Post by Jeeevs2001 on 2006-01-06
Just wanted to say that I have been up till 3 in the morning trying to figure this out! I don't think that "thank you" is sufficient but its the best I can do so .... Thank you for posting this!

---

