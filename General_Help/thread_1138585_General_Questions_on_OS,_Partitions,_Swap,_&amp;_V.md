---
title: "General Questions on OS, Partitions, Swap, &amp; Volume Groups"
date: 2009-04-26
forum: General Help
---

### Post by Th3Professor on 2009-04-26
[SIZE=1]ARG!
OMG! I just wrote a really long message in here and my graphics just flipped out on me, system locked up, and I had to do a cold boot. @#%*&@#%!!!!!!!!!!!!!!!!
I just had to do it again! (...saving this post in text file 1st)
What the heck is up with these graphics/etc. lately?!
I'm running Ubuntu Studio 8.10, with all of the most recent updates for 8.10, I have an nvidia gtx260, with all of the most recent graphics updates. This is getting pretty frustrating... and this didn't start happening 'til Ubuntu 9.04 came out, and I'm not even using 9.04 yet (avoiding it for a couple months to wait on new bugs to be removed, yet it doesn't seem to make a difference in my case). <frustrated with this system>

Okay. Let's see if I can do this again without the p.o.s. graphics drivers or whatever flipping out and locking up on me again.[/SIZE] 

My questions...

I have 5 hard drives:
1= OS (all boots and primary system files)
2,3,4= storage (raid5 & lvm)
5= external (movable storage)

OS:


[LIST=1]
[*] I've installed unix systems before just fine but for some reason it's not working now. How do I get sysV (Solaris), BSD (like OpenBSD), and other linux systems (like Gentoo) to work and also recognize hdd 2,3,4 (not for boot, just recognize and use after booting)?
[*]I have a "solaris boot" on a primary partition and a "solaris" (for all non-boot solaris files) on an extended partition. That should work, right?
[*]How do I include openbsd on the computer without having to sacrifice any of the current sda1, sda2, or sda3 boot options?
[/LIST]
 
Partitions:

sda1 = linux = /boot
sda2 = windows vista (with fuse, which isn't working right now, not sure why)
sda3 = solaris boot (not currently set-up)
sda5 = linux (system files only) = /
sda6 = linux (workspace) = /studio/workspace
sda7 = swap (striped priority with sda8)
sda8 = swap (striped priority with sda7)
sda9 = solaris = not currently set-up
sda10 = linux (for secondary linux system, like gentoo) = not currently set-up
sdb1 = linux raid
sdc1 = linux raid
sdd1 = linux raid
sdi1 = vfat (fat32 default), external storage, used to read as sde1 (that's odd)


[LIST=1]
[*] Is there a more optimal arrangement and allotment of partitions and space for use with Ubuntu Studio, OpenBSD, Solaris, Gentoo, and Windows Vista?
[*]I'd like to see if I can include an OS on the external hard drive without losing and re-copying my current vfat/fat32 stored files. Is there a way to set-up the external hard drive to include a *nix OS without having to format the whole disk?
[*]I tried setting up an encryption type file system (or maybe it was just a folder in /home), yet it doesn't appear to be working. I believe it's mounted as "securityfs". How do I set that up correctly?
[/LIST]
 
Swap:


[LIST=1]
[*] I think that I can use the 2 swap spaces (sda7, sda8) concurrently with solaris (not just linux). Is that right?
[*]That would be excellent if sysv will recognize my current linux swaps. However, do I need separate swap space set aside to work with bsd?
[*]Other linux installs will recognize and use my current swap spaces, right?
[*]Is it possible to have either linux and/or sysv and/or bsd use swap space that is reserved on my raid5 & lvm set-up (sdb, sdc, sdd)?
[*]Why is it that even when my RAM peaks in usage that I still use minimal (like maybe 0.5%) swap?
[*]I have 4GB RAM, so I set up "2x2GB" swaps with equal/shared priorities (striped), instead of "1x4GB swap". I read that striping swap space can be useful so went ahead and went for it, though am not really sure if it's even making a difference. Does it make a difference?
[*]As it is I'm hardly even using swap anyway, it seems useless even on my system's "heaviest" days. There are ideas on using X amount of swap for Y amount of RAM in order to produce "more efficient" results, and yet there are several opinions on just what amount is ideal. Why is that?
[/LIST]
 
Volumes:

My non-OS internal disks (sdb, sdc, sdd) are set-up with linux soft raid (raid5, 128k chunk) via mdadm (/dev/md0), and they're using lvm (matching block/chunk/etc.) for use with 3 separate volume groups (/dev/mapper/vg0-vault (xfs), /dev/mapper/vg0-zone (ext3), /dev/mapper/vg0-nomad (ext3)). The "vault" is primarily storage, while my intention with "zone" is for unix non-boot type files (initially solaris, alternately openbsd), and my intention with "nomad" is for alternate linux non-boot type files (like gentoo or slackware).


[LIST=1]
[*] Can I use those volume groups with any of those systems?
[*]If I cannot use those groups with any of the systems (perhaps due to lvm), how might I apply my raid5 space to those systems (perhaps without lvm)?
[*]Is it possible to set up the raid5 on all 3 of those disks while only using lvm on part of the space, reserving non-lvm (but still raid5) space for use with other systems?
[*]EDIT: (forgot this question) It looked like xfs works really well with my raid5 set-up, is there any real advantage (or disadvantage) to using that over ext3 with this kind of set-up?
[/LIST]
 
Thank you (especially for your patience with reading through all of this, even a bigger thank you for replying with any help that you can provide)!

---

### Post by mb_webguy on 2009-04-26
Wow.  That's quite an infodump.  You may want to consider splitting this up into maybe 3 more specific threads.  You're likely to get more and better answers that way.  But I'll see what I can do...> **Th3Professor said:**
> OS:
[LIST=1]
[*] I've installed unix systems before just fine but for some reason it's not working now. How do I get sysV (Solaris), BSD (like OpenBSD), and other linux systems (like Gentoo) to work and also recognize hdd 2,3,4 (not for boot, just recognize and use after booting)?
[*]I have a "solaris boot" on a primary partition and a "solaris" (for all non-boot solaris files) on an extended partition. That should work, right?
[*]How do I include openbsd on the computer without having to sacrifice any of the current sda1, sda2, or sda3 boot options?
[/LIST] 
1. All you should have to do is make sure those hard drives (or rather the partitions on them) are mounted in each OS.

2. I don't have much experience with Solaris, but from what I remember, it's not picky where it's installed or on what type of partition.  So yes, I don't see why that shouldn't work.  As long as the two partitions are mounted properly.

3. You should just be able to shrink one of the existing partitions and use the newly unused space to make a new one for OpenBSD.

> **Th3Professor said:**
> Partitions:

[LIST=1]
[*] Is there a more optimal arrangement and allotment of partitions and space for use with Ubuntu Studio, OpenBSD, Solaris, Gentoo, and Windows Vista?
[*]I'd like to see if I can include an OS on the external hard drive without losing and re-copying my current vfat/fat32 stored files. Is there a way to set-up the external hard drive to include a *nix OS without having to format the whole disk?
[*]I tried setting up an encryption type file system (or maybe it was just a folder in /home), yet it doesn't appear to be working. I believe it's mounted as "securityfs". How do I set that up correctly?
[/LIST]
1. "Optimal" is relative.

2. Again, you should be able to shrink the existing partition and create a new one.

3. I don't know.
 
> **Th3Professor said:**
> Swap:

[LIST=1]
[*] I think that I can use the 2 swap spaces (sda7, sda8) concurrently with solaris (not just linux). Is that right?
[*]That would be excellent if sysv will recognize my current linux swaps. However, do I need separate swap space set aside to work with bsd?
[*]Other linux installs will recognize and use my current swap spaces, right?
[*]Is it possible to have either linux and/or sysv and/or bsd use swap space that is reserved on my raid5 & lvm set-up (sdb, sdc, sdd)?
[*]Why is it that even when my RAM peaks in usage that I still use minimal (like maybe 0.5%) swap?
[*]I have 4GB RAM, so I set up "2x2GB" swaps with equal/shared priorities (striped), instead of "1x4GB swap". I read that striping swap space can be useful so went ahead and went for it, though am not really sure if it's even making a difference. Does it make a difference?
[*]As it is I'm hardly even using swap anyway, it seems useless even on my system's "heaviest" days. There are ideas on using X amount of swap for Y amount of RAM in order to produce "more efficient" results, and yet there are several opinions on just what amount is ideal. Why is that?
[/LIST]
1. Again, I don't have much experience with Solaris, so I can't answer that part.  You can [use multiple swap spaces on Linux]("http://linux.about.com/od/ptn_howto/a/hwtptn10t02.htm"), but based on one of the questions below, I don't know why you'd need to.

2. If you use the same swap for multiple OSes, the information there will be overwritten by whichever OS you're currently using.  You can use the same swap space for all of the OSes that use swap if you want to do so.  The only problem with doing this is that if you use hibernation on any of those OSes, you can't hibernate and then boot a different OS, because the hibernation data will be overwritten.

3. See the answer to #2.

4. I don't see why not, but it seems to be a bit of a waste to put swap on RAID.

5. It depends on your [swappiness setting]("http://ohioloco.ubuntuforums.org/showpost.php?p=6625272&postcount=2").  It sounds like yours is set pretty high, or else you have way too much swap.  Memory is always going to be faster and more efficient than hard drive space, so systems are generally set up to prefer memory over swap.  If you want to use more swap (which will probably mean a drop in system performance), you can simply increase your swappiness setting.

6. I wouldn't think it would make a difference if the two swap spaces are on the same physical drive.  If they're on separate drives, then you might see a small performance boost.  On the other hand, you don't seem to be using the swap you have.  4GB of memory is pretty big, and it's no wonder you're not using much swap.  If you're not using hibernation, you really don't need swap equal to your memory if you have that much memory available.

7. No two systems are alike.  What works best for you and the way you use your computer won't be optimal for someone else.  If you're using your system as a desktop, have 4GB of memory, and aren't using hibernation, then you really don't need anywhere near 4GB of swap.  On the other hand, if you're using hibernation on a multi-boot system, then you might want a separate swap space for each OS, each equal in size to your memory.  And if you're running a server, an ample amount of swap is generally a good thing.  And of course it depends on the software you're using and how many applications you're running at once.  If you don't multitask much and the software you use isn't very resource-intensive, then you may not *need* any swap at all with 4GB of memory.  On the other hand, if you tend to compile software, transcode video, and use a F@H client all at once, then you might want some swap handy.  It's all relative.  There is no objective "best" solution.
 
> **Th3Professor said:**
> Volumes:
I'm going to leave this section for someone more knowledgeable on the subject to answer.

---

### Post by Th3Professor on 2009-04-27
OS ?s:
> **mb_webguy said:**
> 
[quote=Th3Professor;7152893][SIZE=1]
[/SIZE]1. I've installed unix systems before just fine but for some reason it's not working now. How do I get sysV (Solaris), BSD (like OpenBSD), and other linux systems (like Gentoo) to work and also recognize hdd 2,3,4 (not for boot, just recognize and use after booting)?

1. All you should have to do is make sure those hard drives (or rather the partitions on them) are mounted in each OS.
[/quote]
Nice. So... okay yeah, that makes sense. Solaris can access/use linux-type file systems. D'oh! :)

> **mb_webguy said:**
> 
[quote=Th3Professor;7152893][SIZE=1]
[/SIZE]3. How do I include openbsd on the computer without having to sacrifice any of the current sda1, sda2, or sda3 boot options? 

3. You should just be able to shrink one of the existing partitions and use the newly unused space to make a new one for OpenBSD.
[/quote]
At the moment I'm using all primary partitions. I didn't think you could make more primaries but only logicals. I thought the bsd-types of unix required a primary, or, can bsd (boot and main OS files) be installed on an extended/logical partition?

Partition ?s:
> **mb_webguy said:**
> 
[quote=Th3Professor;7152893][SIZE=1]
[/SIZE]2. I'd like to see if I can include an OS on the external hard drive without losing and re-copying my current vfat/fat32 stored files. Is there a way to set-up the external hard drive to include a *nix OS without having to format the whole disk?

2. Again, you should be able to shrink the existing partition and create a new one.
[/quote]
Excellent!

> **Th3Professor said:**
> [SIZE=1]
[/SIZE]3. I tried setting up an encryption type file system (or maybe it was just a folder in /home), yet it doesn't appear to be working. I believe it's mounted as "securityfs". How do I set that up correctly? 
 
(Crossing my fingers someone can help on this one. I may ask in another thread somewhere.)

Swap ?s:
> **mb_webguy said:**
> 
[quote=Th3Professor;7152893][SIZE=1]
[/SIZE]2. That would be excellent if sysv will recognize my current linux swaps. However, do I need separate swap space set aside to work with bsd?

2. If you use the same swap for multiple OSes, the information there will be overwritten by whichever OS you're currently using.  You can use the same swap space for all of the OSes that use swap if you want to do so.  The only problem with doing this is that if you use hibernation on any of those OSes, you can't hibernate and then boot a different OS, because the hibernation data will be overwritten.
[/quote]
When initially looking at swap options I saw the "Linux swap/Solaris" option and figured the swap could be used in linux and solaris - but not bsd (I should probably know this since I've used bsd extensively but obviously not enough if I can't remember something like this lol, though it *has* been a long time since installing a fresh bsd) - anyway, there doesn't appear to be any other options for swap in fdisk. I think the fact that it listed the swap specifically as "linux swap" is what through me off.

Volume ?s:
> **mb_webguy said:**
> 
I'm going to leave this section for someone more knowledgeable on the subject to answer.
Okay, sounds good. RAID & LVM types of things don't seem to be an uber-popular thing. I originally wasn't going to use lvm, and just use raid5, though after doing some digging discovered lvm's a nice feature and works really well in combination with raid. (Hoping someone can help with the ?s below...)
> **Th3Professor said:**
> [SIZE=1]
[/SIZE]
Volumes:

My non-OS internal disks (sdb, sdc, sdd) are set-up with linux soft raid (raid5, 128k chunk) via mdadm (/dev/md0), and they're using lvm (matching block/chunk/etc.) for use with 3 separate volume groups (/dev/mapper/vg0-vault (xfs), /dev/mapper/vg0-zone (ext3), /dev/mapper/vg0-nomad (ext3)). The "vault" is primarily storage, while my intention with "zone" is for unix non-boot type files (initially solaris, alternately openbsd), and my intention with "nomad" is for alternate linux non-boot type files (like gentoo or slackware).


[LIST=1]
[*] Can I use those volume groups with any of those systems?
[*]If I cannot use those groups with any of the systems (perhaps due to lvm), how might I apply my raid5 space to those systems (perhaps without lvm)?
[*]Is it possible to set up the raid5 on all 3 of those disks while only using lvm on part of the space, reserving non-lvm (but still raid5) space for use with other systems?
[*]EDIT: (forgot this question) It looked like xfs works really well with my raid5 set-up, is there any real advantage (or disadvantage) to using that over ext3 with this kind of set-up?
[/LIST]
 
Thank you (especially for your patience with reading through all of this, even a bigger thank you for replying with any help that you can provide)!

---

