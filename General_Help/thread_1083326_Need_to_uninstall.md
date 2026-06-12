---
title: "Need to uninstall"
date: 2009-02-28
forum: General Help
---

### Post by xrotaryguy on 2009-02-28
I recently installed a slave hard drive on my desktop and can no longer boot the computer normally. The computer usually runs Ubuntu 7.1 or XPSP2. The only way I can booth the computer is with my Ubuntu 7.1 install CD. I have several versions of Ubuntu on this desktop and I would like to remove them and start over. Is there a way I can do this while running Ubuntu from the install CD?

It's an older Compaq with an Intel Celeron. 

By the way, I am still running 7.1 on this computer because 8.1 will not run on it. Evidently 8.1 does not like Celeron processors. Weird.

---

### Post by thtrgremlin on 2009-02-28
These is no "uninstall", per say, but might be able to resolve your booting issue.

Will neither ubuntu nor XP start without using the Live CD, or just one or the other?

If you do not put in the Live CD, what error message, or any message, do you get? (is it from the bios, from grub, or windows boot loader)

If neither will start, and you are getting an error message from grub, can you also post your /boot/grub/menu.lst and /boot/grub/device.map

Sure we can track it down. I've done a lot of installs, and certain machines just don't get setup correctly, and reinstalling doesn't help.

Also, in case you would like to know, 7.10 refers to the release date of October(10), 2007, so just as far as naming goes, 7.1 and 7.10 don't necessarily mean the same thing. Can know what you are talking about because there are only two releases per year. But just in case you were curious about the naming of the version numbers.  :)

---

### Post by thtrgremlin on 2009-02-28
oh, output of ```
sudo fdisk -l
```would also help track this down asap. Thanks.

---

### Post by abn91c on 2009-02-28
its not the celeron processor, my old inspiron 1000 has a celeron, kubuntu 8.10 runs fast(installed by wubi)and Xp SP3, check your video card drivers abd reset your BIOS to default, see If that helps

---

### Post by xrotaryguy on 2009-02-28
xp will not boot and neither will ubuntu :(

The error is from the grub loader I guess:

> 
GRUB Loading stage1.5

GRUB loading, please wait...
Error 22

I will try to figure out where Ubuntu is installed.

And yes, this is 7.10 :)
... now I know how the naming convention works. Thanks for that :)

---

### Post by thtrgremlin on 2009-02-28
resetting the bios settings to default was also a good suggestion (makes sure that isn't the issue) but still some of the stuff posted above.> can you also post your /boot/grub/menu.lst and /boot/grub/device.map
and the output of ```
sudo fdisk -l
```Sorry if those details were a bit hidden, but that will tell what grub thinks it should do. Either way, there is a resolution.  :)

and might as well offer a simple solution. from a live desktop, open a terminal and :```
chroot /media/<disk> /bin/bash
```where <disk> is where ubuntu is installed. Next, ```
sudo update-grub
```That might resolve the problem, but hard to tell without that other output. It also might only let ubuntu start, but not XP. If that is the case, just mention as such.

Look forward to hearing from you. I have had this problem in the past and HATE IT!!! Delighted help someone stress less than I did about figuring out how to fix it.

---

### Post by xrotaryguy on 2009-03-02
I did the sudo fdisk thing in the terminal and got:

> ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors


Maybe I was supposed to enter it in the same screen as my error 22 message?
I'll try that

---

### Post by Ripose on 2009-03-02
That is not the NUMBER 1 it is supposed to be a LOWERCASE L

Have you tried using the GRUB rescue CD?

---

### Post by xrotaryguy on 2009-03-02
Aah... Well that worked better :)

> Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xf235746a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         566     4278928+   b  W95 FAT32
/dev/sda2   *         567       10336    73861200    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81367739

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           2       60801   488376000    5  Extended
/dev/sdb5               2       60801   488375968+   7  HPFS/NTFS


What ever that means...

---

### Post by thtrgremlin on 2009-03-02
Ok, so taking apart what this means:

This is a list of the hard drives your computer sees, some of its properties (heads, tracks, cylinders and such), what the computer calls them (sda, sdb), and such.

So for your purposes, it sees two disks. Your 80GB hard drive is /dev/sda and your 500GB drive is /dev/sdb.

The 80G (/dev/sda) has two partitions. The first (/dev/sda1) is formatted FAT32. The second (/dev/sda2) is formatted NTFS. Both are "primary" partitions. The bios can only boot from primary partitions, and each disk is limited to 4 primary partitions. To get around that, we use a "boot loader" in this case GRUB. The bios starts grub, then grub can boot an operating system on either a primary partition (even one on the same partition as grub), or a "logical" partition. A logical partition is one that can't be seen by the bios because the area of the disk that holds the information about the disks is too small to count past 4. So one of our "primary" partitions can become something called an "extended" partition. You can only have one extended partition per disk, but an extended partition can have as many logical partitions inside of it as you like.

Lets look at the other disk

The 500G (/dev/sdb) only has one partition, an extended partition (/dev/sdb2). On that extended partition, there is one logical partition (/dev/sdb5) that takes up the entire disk, and is formatted NTFS. Notice that the entended partition and the logical partition start at exactly the same byte on the disk. That is because the partition information is actually physically located at the beginning of the disk.

See the '*' symbol? These are partitions that are marked as bootable. Technically, the bios can't tell the difference between a primary partition and an extended partition. All it knows is up to 4 places tne partitions can begin. They can also be marked as bootable. When you start your computer, the bios reads that info at the beginning of your disks and which ever device you picked to boot from, it is going to, basically, pass off control of the computer to the information there on the disk marked bootable. If it doesn't find something, or it doesn't boot, then it goes back to the bios, and reports the error that id can't boot.

So moving past all that technical stuff /dev/sda2 is marked for boot, which I am assuming is your Windows install. /dev/sdb2 is marked for boot, but it is an extended partition, so even if there was something there, it would return in error because you can't boot to extended partitions.

So a few things may have happened. Before, your 80G hard drive had the windows boot loader, and the beginning of the disk said to boot what Linux calls sda2. When you installed ubuntu and installed grub, the bios was told to look somewhere else on the disk for grub, but grub isn't on a primary partition, it is on an a logical partition, so the bios never finds it, grub never starts, so neither OS can be booted.

The CD works, because the bios can find the CD, and the beginning of the CD points to grub. you then use grub to tell the computer where the OS is, either windows or ubuntu and everyone is happy... except you  :)

So how to remedy this situation? easiest I see is to reformat the 500G hard drive (please use a linux file system, like ext3. there are ways to get windows to work with it, but it really hurts your linux performance to not use it when running ubuntu). Let it do its guided setup using the entise disk, then everything should work fine. It seems your bios already wants to boot that disk, so no need for change there, then afterwards can make the necessary additions in order to get grub to see Windows. After that, I can even show you how to get Windows to support ext3 file systems.

I know that was a lot, but I thought you might be interested in what happened, and why things were working the way they were before just telling you what to do. It is more interesting that way, I think, and the computer seems a bit more innocent, and a little less evil with a personal grudge against you.  :)

---

### Post by xrotaryguy on 2009-03-02
And here I was thinking the computer was just toying with me. Bubble burst.

So I'm basically supposed to use this same disc to re-instal Ubuntu? I have actually tried to re-install Ubuntu a couple of times with this disc already and it has not worked.

Also, this re-installation process is supposed to reformat the 2nd hard drive?  

I'll wait for a response before trying this.

---

### Post by xrotaryguy on 2009-03-02
By the way, thanks for all the help thus far. Very insightful stuff. 

I wonder what would happen if Microsoft had a forum like this...

---

### Post by thtrgremlin on 2009-03-03
I do not know why the install disc would make the second drive entirely an extended partition. If you think you can handle it, try doing a manual partitioning. delete the partition and create a primary partition at the end twice the size of your ram at the end of the disc and mark the format at 'swap'. You will know what I mean when you use the manual option (hopefully). Create another partition using all the rest of the space, format it ext3 and set the mount point to '/'. That's it! Proceed with the rest of the install.

Not to worry you, but there is a chance that might still have a problem, and if it does, I know what to do... and it won't require reinstalling. With this having a good chance of fixing things, Lets just see if this works. I am going to see if I can replicate your bug tomorrow and see if it is a problem with the installer.

As far as your M$ question, it would never work, at least not exactly. Its a political thing. Basically, who wants to give their time and energy away for free to help with something Microsoft is paid to do? M$ makes money, while EVERYTHING that is Gnu/Linux is created for someone's personal use and given away for free that others that create will be willing to share in the same way. Additionally, if you make a good program for yourself and share it for free, there is a good chance people will repay you through contributions of bug fixes, additional features, or maybe a really big thank you.

When was the last time you think anyone took the time to write Bill Gates and say "Thank you Bill for making a really great operating system for my computer". Not likely, cause why bother, you got your OS, M$ got their money, no more reason to really talk to each other.

It is really interesting the relationship Sun Microsystems has with the OSS community. They give away a produce for free, and open the source. However, if you contribute, you can only make code suggestions, that may or may not go in, and Sun keeps total control. Lots of people use open office, but there is no real Open Office developer community because you can't really ever be part of a team. They are 'basic' open source, meeting the dictionary definition. They arn't putting their effort into community building. Ubuntu is quite the irony. Sun is open source and discourages community (passively) while Cannonical makes proprietary software (you can't get the code for the forums, or even help) but these closed tools are used to build community.

M$ having a site like this is like having a poetry jam where they charge admission: If you are going to read poetry, you want to get paid. But make it free and charge for drinks, but put in some comfy chairs, people will want to share for free just to be heard.

I love ubuntu. I do some programming, but nothing cool enough worth inclusion in Ubuntu. Maybe some day. I am AMAZED how much Gnu/Linux has become simply through a desire for nerds to share and help each other out. I WANT to be more a part of such a great community, but my experience and skill only put me at, hopefully, very knowledgeable user.  So, I try and do support. I came on the forums for the first time in a long time and found I knew the answers to many of the questions people were asking. So I figured 'why not?'

Seriously, I get this whole, wonderfully incredible operating system and software that does everything I need that would otherwise cost tens of thousands of dollars in proprietary software, and it is all given away in hopes that people will want to get involved.

Me helping any way I can makes me feel a part of that; it is how I can pay for my Linux just the way it was meant to be.

So this is my way of giving back. If there was a site like this for Microsoft (actually, there is, sort of. it is called Microsoft Knowledge Base) I, for one, wouldn't bother. I'd say "Already paid for it, let someone else do it". Why would I want to give my time away for free? This isn't free, I get Linux!

---

### Post by xrotaryguy on 2009-03-06
Ok, so when I'm doing the manual install there's an "edit partition" window. It gives me the options of placing the partition on:

dev/sda1
dev/sda2
or
dev/sdb5

The instructions say that I need at least 2 gigs and dev/sda1 and dev/sda2 do not have enough room on them. Like you said, I should put the new partition on the 500 gig disc. The bios is not set up to install from the 500 gig disc right now though. Will it be ok to leave it like that? Or will I need to set bios to try to boot off of the 500 gig drive first? 

Also, should I use a partition as small as 2 or even 10 gigs? Or do I need to   partition something more like 50% of the disc... or even all of it?

---

