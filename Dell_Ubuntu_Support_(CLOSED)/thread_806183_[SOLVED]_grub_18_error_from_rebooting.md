---
title: "[SOLVED] grub 18 error from rebooting"
date: 2008-05-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yoda akkers on 2008-05-24
I'm a novice at this.

I've installed 8.04 on my dell dimension 8100 (ok its an ancient!) but when I reboot, I get a grub 18 error.

Somebody pls help me?

:(

---

### Post by Patb on 2008-05-24
Yoda, I understand that error has something to do with the bios recognition of the hard drive.  Could you post the following information please.  
How much memory does the computer have?  
What is the size of the HDD(s)?  
Can you boot a live CD on this computer or did you install from the alternate CD? 

If you can boot the live CD, could you please open a terminal and post the output of the following commands:
```
sudo fdisk -l
```

If you can also mount the hard drive, open a terminal and navigate to the directory boot/grub/ on **that mount point**.  This will be a directory something like "/media/sda1/boot/grub/" not just "/boot/grub/".  If you can locate it, post the output of:
```
tail -40 menu.lst
```
As an alternative approach, you might look at this discussion (Google might find more):
[http://ubuntuforums.org/showthread.php?t=6448](http://ubuntuforums.org/showthread.php?t=6448)

Cheers, Pat

---

### Post by yoda akkers on 2008-05-26
Hi thx for that.

Am quite new to linux - only decided to go into it since I used it at university and want to take advantage of it again.

Will check the info and do as you suggested.

Have been pulling my hair out for over a month.  

Have resorted to attempting an install of Warty Warthog since I have an idea that my desktop is so obsolete (Dell dimension 8100 - 1.4Ghz P4) that an obsolete OS may make sense of it.

I was so frustrated with Windows that on my first attempt at installing 7.10 Gutsy i decided to take advantage of installing it on the entire 40Gb hard drive.

Since then I've taken it into school and a 14 year old kid has given me his 160Gb hard drive to check if its the hard drive playing up. Still the same Error 18.

My brother did tell me that Dell BIOS isnt as flexible as most desktops in that they cant be edited that much. Speaking of BIOS I havent updated it over the last 8 years i've had the machine and I cant now since Ive not got windows to downlaod it to my machine.

Re Live CD (this may be a good indicator as to my expertise or lack thereof.. ) do u mean the one you can run Ubuntu from withou installing?

Thanks for your help!

---

### Post by yoda akkers on 2008-05-26
Ok looks like installing the Earliest version doesnt seem to work.

Ho-hum

So Ive booted from the live CD

When you suggested that i type the sumo fdisk command in by opening a terminal..errm how exactly do i open a terminal?

cheers

---

### Post by yoda akkers on 2008-05-26
Hi again

Ive got 384MB RDRAM

and hard drive is 160GB Maxtor

Oh and I opened the terminal and typed the command in here's the response:

To run a command as administrator (user "root"), use "sudo <command>".

See "man sudo_root" for details.



ubuntu@ubuntu:~$ sudo fdisk -1

fdisk: invalid option -- 1



Usage: fdisk [-b SSZ] [-u] DISK     Change partition table

       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)

       fdisk -s PARTITION           Give partition size(s) in blocks

       fdisk -v                     Give fdisk version

Here DISK is something like /dev/hdb or /dev/sda

and PARTITION is something like /dev/hda7

-u: give Start and End in sector (instead of cylinder) units

-b 2048: (for certain MO disks) use 2048-byte sectors

ubuntu@ubuntu:~$ 


Bearing in mind this is after I went throught the installation of 4.10 and ran the LIVE cd for 8.04

Since then I've decided to re install 8.04

Hope this is makin sense

---

### Post by Patb on 2008-05-26
> **yoda akkers said:**
> fdisk: invalid option -- 1
Yoda. Whenever you can, copy and paste commands rather than retyping them.  That command was "sudo fdisk -l" (lower case L) not "sudo fdisk -1".  You will notice the error message has this option listed too: "fdisk -l [-b SSZ] [-u] DISK List partition table(s)"  (although the English always leaves something to be desired, doesn't it. :)).  

> Re Live CD ... do u mean the one you can run Ubuntu from without installing?
Yes, live CD means one on which you can boot a working operating system.  

Your hardware statistics seem okay (just).  If you can follow the suggestions at my post #2 on this thread, someone might be able to make suggestions for how to get your system up and working.   Forget the bios for now, although you might need to come back to that.  Good luck.  

Cheers, Pat.

---

### Post by yoda akkers on 2008-05-27
Thanks for that...

Am running a memory test via the 8.04 disk .. is it meant to go on endlessly until you stop it yourself?

Its been going on for almost 7 hours now, passed 27 tests and 0 errors..

---

### Post by yoda akkers on 2008-05-28
Ok this is what happened..

Out of my frustration I decied to delve deeper into BIOS when I noticed the following:

Primary Hard drive 0 : 49MB  (!?!) 

Because its a DELL and its BIOS A02 it doesnt give me any options to do much...so i decided to try and confuse it.

I entered some specs in for a "phantom" Primary Hard Drive 1 (gave it 8300 cylinders etc...) 

I then went to reboot whereby the BIOS started going into a hissy fit. I went back into BIOS and noticed it had turned of the Primary Hard Drive 1 that I made up BUT!!


It had decided to set the drive 0 to "detect" to actually find out its size..

I exited BIOS and lo and behold... i completed the installation...

All I want to say is after a month of faffing around.. its very rewarding to see the Ubuntu load up screen with no CD in the drive..

I've finally ascended to the realm of the Ancients...

yahay!!

thx for your help!!!

btw here's the response from your fdisk command:

Disk /dev/sda: 160.0 GB, 160000000000 bytes

255 heads, 63 sectors/track, 19452 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x9dc96e9e



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1          31      248976   83  Linux

/dev/sda2              32       19452   155999182+   5  Extended

/dev/sda5              32       19452   155999151   8e  Linux LVM



Disk /dev/sdb: 2017 MB, 2017984000 bytes

4 heads, 16 sectors/track, 61583 cylinders

Units = cylinders of 64 * 512 = 32768 bytes

Disk identifier: 0x00000000



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1   *           1       61584     1970679+   e  W95 FAT16 (LBA)

ubuntu@ubuntu:~$

---

### Post by meierfra. on 2008-05-28
Brilliant!

---

### Post by Patb on 2008-05-29
> **yoda akkers said:**
> All I want to say is after a month of faffing around.. its very rewarding to see the Ubuntu load up screen with no CD in the drive..
Love it,Yoda!  This especially, but also the rest of your exploits made my day.  (I should know, I do SO much faffing around, myself!)  Thanks for posting.  Cheers, Pat.  

(PS: Didn't I mutter something vague about bios in my initial response?! :). But I wasn't onto it, was I.  Glad you fixed it.)

---

