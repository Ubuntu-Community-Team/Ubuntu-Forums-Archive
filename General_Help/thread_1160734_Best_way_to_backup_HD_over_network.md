---
title: "Best way to backup HD over network?"
date: 2009-05-15
forum: General Help
---

### Post by Jengu on 2009-05-15
I bought a new HD for my laptop, and I'd like to backup the existing one to my desktop. I don't have a drive enclosure to let me just hook the laptop drive straight to the desktop, or two drive connectors to allow me to hook two drives to the laptop at once, and the laptop HD contains too much data for me to just burn it all to DVDs, and I don't own any big external drives. So I'd like to 'stream' a backup of my laptop HD to my desktop (both comps are running ubuntu of course). I'm sure this can be done with ssh and scp, but I'm not sure how exactly. I want to copy the drive *exactly* on a preserves-partitioning level (I know I'll have to resize them later), but I don't know how to do that without making a big file all at once then transferring it (and obviously the drive isn't big enough to store its current files plus a copy of itself :P). Anyone know the best way to do this?

---

### Post by kidders on 2009-05-17
Hi there,

You could mount an NFS share and use **dd** to dump the contents of your laptop's currently installed hard disk onto it. There are a few things to watch out for though ...

**Disk image consistency**
Since you don't want to copy at the file level, *you'll* need to ensure that the disk dump is in a relatively consistent state ... Linux's filesystem management won't be able to do it for you. The best option is to boot your laptop from a CD, so that the filesystems on your hard disk can remain unmounted during the copy. A distant second-best option would be to shut off absolutely every process you don't need (ie your graphical environment, all logging, servers, etc.), to try to ensure that your filesystems are written to as little as possible (if at all) during the copy.

**Checking the copy**
You won't be able to do this if your laptop's filesystems were mounted while you copied them, which is one of the reasons booting from a CD would be so much better. Use **md5sum** to verify that your disk & disk image really are identical. It'll take a long time for both your desktop & laptop to perform the checksum calculation, but it's well worth the wait!

**Performance**
Naturally, you should avoid wireless network connections like the plague. You should also try to make sure that all your block sizes match up as cleanly as possible. For example ...[LIST]
[*]Your NFS rsize/wsize settings should match the block size you specify for **dd**.
[*]The destination filesystem's block size should be an integer multiple of **dd**'s block size ... eg 1x, 2x, but not 0.5x.
[*]The filesystem block sizes on your laptop are irrelevant.
[/LIST]The point is to try to ensure that one disk read triggers a single NFS operation, and that in turn results in no more than one write operation on the other end. These settings won't normally affect the accuracy of the copy, but if we're talking about transferring 10s or 100s of gigabytes, there's a very significant performance gain to be had if you get them right.

**A note on scp**
Unless the network you're using is not private, you should avoid copying over an encryption layer ... it dramatically increases the time it would take to copy your data. If you don't like NFS, FTP would be another good (ie low-overhead) option, designed to handle very large transfers. In any case, I'm not sure **scp** could be used at all in this situation, given that you don't have enough wiggle room to create a disk image in advance of copying it.

Anyhow, I hope that helps.

---

### Post by Jengu on 2009-05-18
kidders, thanks for the detailed help! Using a live cd so the laptop file system isn't mounted is a great idea. I don't see though how your solution avoids the laptop having one huge file on it holding its whole contents though, the 'streaming' part. If I tell dd to create an image of the laptop HD and say to save the file on the desktop is dd + NFS smart enough to do that automatically?

---

### Post by lavinog on 2009-05-18
I prefer rsync
```
rsync -auvP ~/ sshcomputer:/homebackup
```
I think that is right...I am on a fresh install so I don't have my backup scripts installed yet.

a usb adapter is handy to have though.
This little thing is handy to have...it works for desktop and laptop drives:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16812119244](http://www.newegg.com/Product/Product.aspx?Item=N82E16812119244)

---

### Post by kidders on 2009-05-19
> **Jengu said:**
> I don't see though how your solution avoids the laptop having one huge file on it holding its whole contents thoughI'm not 100% sure I understand. Dd doesn't create any temporary files, so dumping your laptop's hard disk directly to a network share won't use any local disk space at all.  As for NFS, it works more or less the same way as other file sharing protocols. The reason for choosing it is that it's more likely to be able to handle very large files without breaking.

Once you're booted with your live cd ...[LIST]
[*]Run **mount** to ensure that your laptop's hard disk hasn't been automatically mounted.
[*]Mount a network share (eg /mnt/desktop).
[*]Identify your laptop's disk drive (eg /dev/sda) and dump it straight to /mnt/desktop.
[/LIST]

I hope that's a bit clearer.

---

### Post by Jengu on 2009-05-23
> **kidders said:**
> I'm not 100% sure I understand. Dd doesn't create any temporary files, so dumping your laptop's hard disk directly to a network share won't use any local disk space at all.  As for NFS, it works more or less the same way as other file sharing protocols. The reason for choosing it is that it's more likely to be able to handle very large files without breaking.

Once you're booted with your live cd ...[LIST]
[*]Run **mount** to ensure that your laptop's hard disk hasn't been automatically mounted.
[*]Mount a network share (eg /mnt/desktop).
[*]Identify your laptop's disk drive (eg /dev/sda) and dump it straight to /mnt/desktop.
[/LIST]

I hope that's a bit clearer.

I tried it out today but ran into a new problem, thread here: [http://ubuntuforums.org/showthread.php?t=1168023](http://ubuntuforums.org/showthread.php?t=1168023)

---

### Post by jdaum on 2009-06-28
Hi,

I want to do the same, i.e. backup laptop to desktop, but a question and 3 more problems:

How do I md5 my laptop drives? just md5 /dev/sda1 ?


Additional problem 1) My Desktop is Windows based, would you recommend to use smb to connect?

2) My harddisks are 500GB in total, but only ca 80GB used, what is the best method to get my backup file size down. I thought that gzip would obviously work

3) How do I md5 the zip file on the desktop. I guess this is not the best question here, but I would need something like md5-in-a-zip without it unpacking everything in memory. Any other options?


Kind Regards,

Jochen

---

### Post by kidders on 2009-06-28
Hi there,

> **jdaum said:**
> How do I md5 my laptop drives? just md5 /dev/sda1 ?Try **md5sum /dev/sda**. Hashing /dev/sda1 would only give you a value for one partition. 

> **jdaum said:**
> My Desktop is Windows based, would you recommend to use smb to connect?Afaik, Windows has all kinds of problems with large files, so there are a few reasons why that may not work (eg LFS not enabled, or a local filesystem that can't handle big files). Give it a try & see what happens, I suppose. :???:

> **jdaum said:**
> My harddisks are 500GB in total, but only ca 80GB used, what is the best method to get my backup file size down. I thought that gzip would obviously workYep... that's what I would do. Gzip gives you a reasonably good balance between speed & efficiency, and is widely supported (ie you should have no trouble decompressing it in minimal environments like system rescue CDs). As you probably know, "best" could either mean "most efficient" or "fastest", two properties that tend to trade off against each other.

If your primary concern is compression efficiency, please post back & say so. You see, depending on what's on your laptop's hard disk, you may or may not have a better option.

> **jdaum said:**
> How do I md5 the zip file on the desktop.Normally, I would suggest trying **zcat /path/to/gzipped/backup | md5sum -** ... it's something I've never tried on such a big file though. The trouble is that (out of the box, at least) your Windows box won't have zcat/md5sum on it, so you may have to run the test from your Linux box, which would probably be tediously slow.

I hope that helps.

---

### Post by jdaum on 2009-06-28
Hi,

> **kidders said:**
> Hi there,

Try **md5sum /dev/sda**. Hashing /dev/sda1 would only give you a value for one partition. 

Afaik, Windows has all kinds of problems with large files, so there are a few reasons why that may not work (eg LFS not enabled, or a local filesystem that can't handle big files). Give it a try & see what happens, I suppose. :???:

Yep... that's what I would do. Gzip gives you a reasonably good balance between speed & efficiency, and is widely supported (ie you should have no trouble decompressing it in minimal environments like system rescue CDs). As you probably know, "best" could either mean "most efficient" or "fastest", two properties that tend to trade off against each other.

If your primary concern is compression efficiency, please post back & say so. You see, depending on what's on your laptop's hard disk, you may or may not have a better option.

Normally, I would suggest trying **zcat /path/to/gzipped/backup | md5sum -** ... it's something I've never tried on such a big file though. The trouble is that (out of the box, at least) your Windows box won't have zcat/md5sum on it, so you may have to run the test from your Linux box, which would probably be tediously slow.

I hope that helps.

Thank you for the detailed answers. I will go through these steps and then run the md5 from a live cd as well.

Kind regards,

Jochen

---

