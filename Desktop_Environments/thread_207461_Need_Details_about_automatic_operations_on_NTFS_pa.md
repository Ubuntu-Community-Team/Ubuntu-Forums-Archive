---
title: "Need Details about automatic operations on NTFS parititions / NTFS data loss(!!!)"
date: 2006-07-01
forum: Desktop Environments
---

### Post by greyhat on 2006-07-01
Recently I had installed Ubuntu 6.06 on my laptop in a dual boot configuration, and for the first few reboots really enjoyed my linux system.  The ntfs partition was automatically listed in Ubuntu, and I was able to copy over my Firefox bookmarks and play a few tunes while messing with things in Ubuntu.  Disaster struck, when I rebooted, intending to boot back into Windows XP.  If I selected Windows XP on the grub menu, nothing happened.  (I believe it went to a black screen.) I believe what happened next was I booted back into Ubuntu and my ntfs partition no longer appeared, although I might not have done this step here.  

I tried using the Windows XP setup disc's fixmbr command to remove grub and get back into Windows, but this didn't seem to replace grub or do anything in particular.  Thinking my linux partitions were possibly interfering with Windows XP's boot process, I removed my ext3 / and swap partitions, and tried again.  I also tried an ubuntu live cd at this point, which showed my drive as unrecognized, and I could not force it to be mounted as ntfs either.  I was able to recover 90-95% of my data through a tool called Ontrack EasyRecovery, but I had not indication of the exact problem or steps it took to find the files, only that I could now copy them to my USB hard drive, and then do the tedious day long process of setting up Windows, restoring my data, reinstalling my programs, and changing every little setting.  :( 

Anyhow, on to my questions.  **What does Ubuntu do automatically with ntfs partitions?  And does anyone have any idea what the heck happened? ** I was always one to scoff at reports of "*lunix killed my computer!*" and figured they didn't follow instructions correctly or something similar, but now it appears I have been bitten too.  I would appreciate any help on this so I can get back to trying to switch away from Windows XP for my main desktop. 

Thanks ahead of time. :)

---

### Post by greyhat on 2006-07-02
Bump.  Would really appreciate help so I can try Ubuntu again!

---

### Post by greyhat on 2006-07-02
Bump.  One last try =|

---

### Post by kinematic on 2006-07-02
i don't have a clue what happened.....just wanna say i think it's funny how windows users seem to think it's the end of the world if xp doesn't wanna boot anymore.
just format the entire drive in ext3 and be done with it ;)

---

### Post by greyhat on 2006-07-02
It wasn't really the "Windows" so much as the **night of data recovery**, **entire day it took to format and reinstall**, and **40-50 GB of personal data that was temporarily black holed**, and the fact that as far as I can tell, I *did nothing whatsoever to cause the partition to dissappear*.

---

### Post by praxis22 on 2006-07-02
[QUOTE=greyhat]Bump.  One last try =|[/QUOTE]

Last I heard reading from a NTFS file system was OK, but writing was experimental. If  you want to swap data between partitons you're advised to create a seperate FAT32 filelsystem and use that as a common drive. Since this is well known and understood.

From the status page:
[http://wiki.linux-ntfs.org/doku.php?id=status](http://wiki.linux-ntfs.org/doku.php?id=status)

It looks like they now have a semi stable NTFS write in the works though whether this is the stuff built into ubuntu or not I have no idea, depends on when they last baselined  I guess.

I'd avoid using NTFS under Linux unless you like living dangerously at present.

later
jb

---

### Post by greyhat on 2006-07-02
> Last I heard reading from a NTFS file system was OK, but writing was experimental.

That's the thing -- as far as I know, I didn't do any NTFS writes at all.  I didn't think I could possibly cause problems just by *reading* ntfs, but evidently not...

---

### Post by chalex on 2006-07-02
IIRC, the NTFS partition gets mounted as read-only by default.  I don't have one to try it.  Reading from it certainly shouldn't do anything bad.

Have you checked your disk for integrity using the manufacturer's utility?  Maybe your disk is going bad.

---

### Post by Thund3rstruck on 2006-07-02
It's definately not linux that damaged your hard disk. The drive is mounted as read-only. 

The usual hardrive troubleshooting applies. 

1. Boot into your BIOS, do a probe for your hard drive and validate it's seen
2. Verify it's seen by your OS

```

mount|grep ntfs
sudo hdparm -g /dev/sda2 (or hda1/2 for EIDE)

```
3. If its there then check for it in fstab

```

cat /etc/fstab|grep ntfs

```

---

### Post by greyhat on 2006-07-02
> Maybe your disk is going bad.

The hard drive is physically just fine, I ran SpinRite and Maxtor diags on it, both of which verified it was ok.  

> It's definately not linux that damaged your hard disk.

So what did?  The hard drive does work *now*... It wasn't that the hard drive wasn't detected, it was that the ntfs partition suddenly became an unknown and unmountable partition.  I can't run any linux commands on it currently as its now running just Windows.  Like I said, I am trying to determine *why* I had the original problem, so I can decide whether I want to mess with Ubuntu ever again...

---

### Post by Thund3rstruck on 2006-07-02
Unfortunatly its rather impossible to identify what was going on with your system without access to /var/log files. Perhaps if you'd like to experiment with Linux you should install on a VMWare server terminal.

---

