---
title: "Help remote partition"
date: 2008-12-18
forum: General Help
---

### Post by wyth on 2008-12-18
I'm very familiar and comfortable with partitioning.  However, my parents are not.  Allow me to break it down:

[LIST]
[*]Parents are running Ubuntu on an older Dell.  This was once a dual-boot machine
[*]After not booting into Windows for two years, we decided to nix the Windows partitions and claim that space for Ubuntu -- necessary for 8.10
[*]Problem #1: I live half a continent away.  I VNC into their machine and maintain it, and frankly they're not capable of using a live cd.  Besides,
[*]Problem #2: Something seems to be screwy with their boot sequence in BIOS, and they can't boot to a live cd anyway.  My brother attempted to fix this for them, but nothing seemed to get it to work.
[/LIST]
I'm willing to have them send me the hard drive; that's how I put Ubuntu on it in the first place.  But I seem to remember from way back when a command line way to set partition changes to occur on a reboot.   This allows one to tell the machine what you'd like the partitions table to look like, with the partitions mounted, but when the machine restarts and those partitions are no longer mounted, all the real magic occurs.

However, I'm afraid that might have been a Windows 2000 trick, and I just don't recall -- although if it could be done on Windows 2K, I don't see why it can't be done on Linux.  Is this possible with fdisk or some other tool?  I've been searching for some time, and have come up blank.

There are two main paritions and an extended partition, with the following adjacent blank spots that I'd like to merge with the linux partitions:


                                                               
[CENTER]**[COLOR=Red]10 Gb unallocated | 5 Gb /dev/sda2[/COLOR]** 

[COLOR=Blue]{ E X T E N D E D  P A R T I T I O N }[/COLOR]
[COLOR=Blue]**| 1.2 Gb swap | 9.3 Gb /dev/sda6 | 12.7 Gb unallocated**[/COLOR]
[/CENTER]
 

[COLOR=Black]So the ultimate goal here is to give the 10 Gb unallocated over to /dev/sda2, and the 12.7 Gb unallocated over to /dev/sda6.  They don't need much space, and I'm not concerned with the aesthetics of their partition table, just as long as they can email and chat and write documents and download the occasional podcast and my dad can keep building his fishing database.   (There's actually more than enough space left right now in their /home directories in the extended partitions, but not enough for me to introduce them to anything like video podcasts.)  

As I said, if need be, I'll have them ship me the drive and do it myself with my gear, but if there is a command line trick that'll allow me to make these changes occur remotely on a reboot, sweet jeebus I'd love to know it.
[/COLOR]

---

### Post by wyth on 2008-12-18
just gonna bump this.

---

### Post by bodhi.zazen on 2008-12-18
I moved your post to it's own space as it really has little to do with background information.

I would first say, if it is not broken, don't fix it. You need some way to boot your parent's box and obtain remote access.

It they are not tech savvy, pull the HD and ship it.

---

