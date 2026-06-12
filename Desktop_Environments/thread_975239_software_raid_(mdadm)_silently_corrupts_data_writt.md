---
title: "software raid (mdadm) silently corrupts data written to it"
date: 2008-11-08
forum: Desktop Environments
---

### Post by mattias.jn on 2008-11-08
The Problem
My software-raid-6-array silently corrupts data written to it. It was created with mdadm

Background
After years as a Ms slave I decided that my new computer would be a Linux machine and that I'd also make it my NAS with a nice raid-6-array. So I bought my hardware and built my dream-machine. New, nice and almost completly silent. Ubuntu works like a charm. The problem is that my newly configured software raid doesn't work, at least not in reality. According to istself (/proc/mdstat) it feels fine but accoridng to my tests it's really nasty and repeatedly corrupts 70% of anything I put on it...

Every now and then when I restart Ubuntu it also says that 'md0 unclean shutdown' and it stops in the boot process saying something in the lines of fsck died with exit status 4, you need to run fsck manually to fix the broken file system. Once you've done that nothing really changes...

I've googled my eyes out and tried to fix this by myself and with help from friends far more versed in linux than I am. To no awail. So now I ask you, the ubuntu community, can you help me?

Distribution
    * Ubuntu 8.10 (x86) 32bit

Hardware
    * 6 x 250GB SATA drives, Seagate Barracuda 7200.10, sd[a-f], to be the raid-6-array.
    * 1 x 1TB SATA drive, Seagate Barracuda 7200.11,sdh, ext3, holding the stuff thats supposed to be on the raid
    * 1 x 200GB SATA drive, Maxtor ??,sdg, for system (dual boot Vista/Ubuntu 8.10)

Motherboard
    * Gigabyte GA-X48-DS5, Bios version: F7
      [http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=2766](http://www.gigabyte.com.tw/Support/Motherboard/BIOS_Model.aspx?ProductID=2766)

Graphics
    * Geforce 9600GT Silent, 512MB

RAM
    * 2 x 2GB, Corsair XMS2 DDR2

CPU
    * Intel Q6660, 2,4 GHz

What I have done/tried so far
    * memtest on the ram for 96h, no errors found
    * extensive SMART-testing on all the raid-drives
          - this will be done again, missed something?
    * re-installed ubuntu 8.10 on another disk and rebuilt the array, no change
    * upgraded bios from F5 to F7, no change
    * changed the raid-array from raid-6 to raid-5 to raid-0, Data is corrupt on all 3
    * reformated the filesystem (ext3) on the array, no change
    * Fixed the filesystem manually at least three times, no change


How-To verify the error persists
    * 'rsync -cav /media/samurai/{my media folder}/ /media
      /yukio/{my media folder}/'
      This rsync command which checks checksums on the files as 
      well as timestamps can run for ever since it always fails 
      on the checksums since the previously written data is 
      silently corrupted on write
    * Try and unrar a file...
    * just reboot, I never reach the login screen. Instead I get 
      a recovery terminal which says something in the line of 
      'fsck died with exit status 4 you need to run fsck
      manually"
          - This only happen when the raid-array is set to
            automount in /etc/fstab

Questions
    * What can cause this?
    * Have I missed anything in my troubleshoting?
    * Is there a serious flaw/bug in mdadm and ubuntu 8.10 that 
      I've missed?

---

### Post by mattias.jn on 2008-11-10
Problem solved. After a lot of grief I decided to try what shouldn't happen, ie one of the hard drives are broken without the raid noticing...

So I split the raid-6 in two raid-5 sets, found that one of the sets corrupted data... so I split that one in to the three different drives and tested them individually, which proved that one was broken. I took that disk an swapped it around a bit on the motherboard to ensure that it in fact was the disc that was broken. Satisfied with that I put it in my old win XP box which confirmed the same thing... A silently broken hard drive!!

Now I'm seriously looking in on raidz2 which is "zfs with raid6"...

Thanks to all who devoted some brain-power to this issue!

---

### Post by whatever69 on 2009-01-04
I've also been receiving the "fsck died with exit status 4" and I have a RAID 5 setup with 4 drives using mdadm.  Only recently (last 2 months) have I started getting this message.  

Is there a way to test to see if indeed a hard drive is "silently" damaged?  I mean, mdadm job is to detect this exact thing.  Heck I don't even want to blame mdadm if it isn't.  But something is fishy here.  I really don't want to start moving hard drives around and messing around with my array for no reason.

---

### Post by mattias.jn on 2009-01-05
Well, the problem is that in order to check the drives individually you have to "split up" your mdadm raid in to smaller raids and then use rsync -cav to copy testdata between two disks/raid-sets. If the checksums aren't the same, you've got silent corruption. 

The problem is that this will destroy any data on your current raid. The whole "silent corruption error" is a messy one, since it doesn't show up on any "normal" tests and if you have a raid-array with one damaged drive this will corrupt the entire raid-array and to check the disks in the array you have to split up the array =(

I'm no linux-magician but from what I read during the the two weeks I was struggling with this error I found no info on anything spotting/fixing silent corruption except the ZFS-filesystem, which I now use through Fuse (yeah it's slow, but reliability is worth it), whith raidz2 (ie raid 6).

If you find a solution, please remember to post it in this thread ;)

---

### Post by whatever69 on 2009-01-05
I just ran
```

$blkid
```

and the results were different than the /etc/blkid.tab file!  my raid array entry was missing the XML attribute *SEC_TYPE="ext2"*.  I forget what else.  I also had an entry for squashfs ... no clue what that is.  Either way, deleted that file after some googling and rebooted.  Now both /etc/blkdid.tab and blkid match.  The squashfs entry is no longer there.  I think that as I upgraded Ubuntu versions, this file was not updated.

I'm also guessing that the UUID produced by running blkid is not supposed to be the same as the UUID that mdadm produces when you run

```
$sudo mdadm --detail /dev/md0
```

I'd love to compare notes to see if indeed the UUID by blkid is supposed to be the same as the one produced by mdadm.

I also get the following:

```
$ sudo mdadm -E /dev/md0
mdadm: No md superblock detected on /dev/md0.
```

So lots of little funkiness going around that could easily mask the true case.
 
I don't have any extra drives, so I can't run those tests you mentioned since my raid array is 75% full.  It's 5x320GB and over 2 years old.  I think I'll just be selling all my drives and buying 2 1 TB drives in mirror mode.  It'll cost me less $$ and time.  Btw, I went in and deleted a whole bunch of files/folders that were damaged and have forced fsck on my array for several reboots.  So far so good.  No such errors.

I actually only figured out the corruption when I was watching a movie (divX) and suddendly midway, the audio was out of sync.  The file had been silently damaged.  I went through many, many files removing them.

It's a shame really because I think my raid 5 array has been excellent for 2years+.  Oh, and I also write to it via Samba from windows and via NFS from OS X.

Here's hoping fixing blkid.tab and removing the corrupt files/folders will make this bug go away.

---

