---
title: "Synaptic Error"
date: 2008-10-16
forum: Desktop Environments
---

### Post by mulluysavage on 2008-10-16
I'm trying to run ms-sys to boot from XP. I downloaded the ms-sys package, then pointed Synaptic to the local directory where I unpacked it by entering it in the 3rd-party repositories. Synaptic crashed, and won't open again. Each time, I get the error:

E: Malformed line 29 in source list/etc/apt/sources list (dist parse)
E: The list of sources could not be read
Go to the repository dialog to correct the problem
E: _cache->open()failed, please report

How can I get synaptic running again? how can I run ms-sys (I've been trying from the terminal, no success.)

---

### Post by sisco311 on 2008-10-16
open a terminal and post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by mulluysavage on 2008-10-16
ubuntu@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Xubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-updates universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports restricted main multiverse universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy-backports restricted main multiverse universe

deb file://media/My Book/mssys

---

### Post by sisco311 on 2008-10-16
edit the file:
```
gksu gedit /etc/apt/sources.list
```and delete the last line: *deb file://media/My Book/mssys*
then run:
```
sudo aptitude update
```

what are you trying to accomplish?

do you want to uninstall ubuntu and single boot windows
or dual boot ubuntu and windows?

---

### Post by mulluysavage on 2008-10-16
Thank you I will try that when I get home I'm at work now.

I am trying to boot from XP again. I am moving to a new machine and want to get this one back on xp and get linux totally off it. If you know a better way to do this that would be great.

---

### Post by sisco311 on 2008-10-16
[http://www.users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_uninstall_Ubuntu]("http://www.users.bigpond.net.au/hermanzone/p18.htm#If_you_are_about_to_uninstall_Ubuntu")

---

### Post by mulluysavage on 2008-10-16
Cool. This is exactly the page from which I got the idea to use ms-sys. I'm working off Live CD - Ubuntu won't boot off HD, and neither will Windows - because the MBR is not pointing to it. So I want to run ms-sys and redirect to windows.

But I can't seem to get ms-sys to install - How do I get the ms-sys that I downloaded to be recognized by synaptic?

The first command you gave me to run doesn't do anything....

Thanks for your help!

---

### Post by mulluysavage on 2008-10-16
p.s. I don't have a XP boot cd so that's why I want to use ms-sys

---

### Post by mulluysavage on 2008-10-16
Okay, I used the GUI to find the sources.list file and deleted the line you suggested. I added that line trying to point Synaptic toward the ms-sys file that i downloaded. Synaptic runs again. How do I get synaptic to find and install ms-sys? I have tried the command-line way with no success.

---

### Post by sisco311 on 2008-10-16
download the deb file from: [http://packages.debian.org/etch/ms-sys]("http://packages.debian.org/etch/ms-sys")
double click on the file to install it.

---

### Post by mulluysavage on 2008-10-16
Great. I ran ms-sys and got a warning, and I don't know if I want to force an MBR overwrite. I figure that /dev/sda1 is the windows boot sector, but the warning tells me that its "probably a partition device." Can I get some other eyes on this before I force? Thanks!

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x65dd65dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   117210239    58605088+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   913809329   456904633+   c  W95 FAT32 (LBA)
/dev/sdb2       913809330   976768064    31479367+   5  Extended
/dev/sdb5       913809393   974085209    30137908+  83  Linux
/dev/sdb6       974085273   976768064     1341396   82  Linux swap / Solaris

Disk /dev/sdc: 1031 MB, 1031675904 bytes
16 heads, 63 sectors/track, 1999 cylinders, total 2014992 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63     2013983     1006960+   6  FAT16
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo ms-sys -m  /dev/sda
ubuntu@ubuntu:~$ sudo ms-sys -m  /dev/sda1
/dev/sda1 seems to be a disk partition device,
use the switch -f to force writing of a master boot record
ubuntu@ubuntu:~$

---

### Post by sisco311 on 2008-10-16
run the command on /dev/sda:

```
sudo ms-sys -m /dev/sda
```

in linux the default behavior is no output to a terminal unless there are errors.

---

### Post by mulluysavage on 2008-10-16
Ran ms-sys on /sda and rebooted. Got the DOS -looking progress bar that preceeds XP launch and then nothing. No disk activity. Wrong reference I guess? I guess I could try other partitions...

---

### Post by mulluysavage on 2008-10-17
Since this hasn't worked, I think I'm going to try Super Grub Disk.

---

