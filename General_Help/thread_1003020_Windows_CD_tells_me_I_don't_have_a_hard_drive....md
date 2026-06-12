---
title: "Windows CD tells me I don't have a hard drive..."
date: 2008-12-05
forum: General Help
---

### Post by Gonz_91 on 2008-12-05
Hi everyone!


Today, I thought I'd wipe my hard drive clean, and then, I'd install windows, shrink its partition, and then I'd partition for Ubuntu: Swap, Root and Home partitions.

But, after I cleaned the hard drive and booted into the windoze CD, it tells me it can't find a hard drive!

Any help?


(sorry if I posted on the wrong section :|)

---

### Post by adult swim on 2008-12-05
you may need to format the drive to NTFS to get the windows install disk to see it.

---

### Post by cmay on 2008-12-05
> **Gonz_91 said:**
> Hi everyone!


Today, I thought I'd wipe my hard drive clean, and then, I'd install windows, shrink its partition, and then I'd partition for Ubuntu: Swap, Root and Home partitions.

But, after I cleaned the hard drive and booted into the windoze CD, it tells me it can't find a hard drive!

Any help?


(sorry if I posted on the wrong section :|)

i think the problem can be solved by using fat file system for the first partion on the harddisk. windows can not find a unallocated partion or a partion in linux file system . as i remember it do not hang me up on it however as i have not messed wiht windows for 3 years by now. 
good luck :).

---

### Post by Gonz_91 on 2008-12-05
well, then, I'm reformatting the whole thing to NTFS. I'll update soon.

---

### Post by Hyper Tails on 2008-12-05
Once I had the same issue but it detected my hardrive and the partition for vista was a ntfs and It fefused to install
so I had no choice to delete Vista :cry:

WHATS Up WITH THAT!!! 
:cry: :cry: :cry:

---

### Post by adult swim on 2008-12-05
it will go way faster if you delete all of the partitions first and then do the format.

---

### Post by Yellow Pasque on 2008-12-05
Strange. Make sure the BIOS still sees the drive. You might also try creating an NTFS partition with a LiveCD (ubuntu livecd will need the ntfsprogs package for that).

Also, what version of Windows are you trying to install, and what kind of hard disk (SATA or PATA) and motherboard do you have?

Edit: I got distracted and 10 other people posted before I hit the post button. (sorry)

---

### Post by Gonz_91 on 2008-12-05
> **adult swim said:**
> you may need to format the drive to NTFS to get the windows install disk to see it.
Done. Formated to NTFS. Still nothing. Windows XP CD says I have no hard drive installed.


I knew windows was dumb, just not this much.
On the other hand, I'd really like to have, just in case....


So, any other ideas? Is there something I might have done wrong?

---

### Post by Gonz_91 on 2008-12-05
> **Temüjin said:**
> Strange. Make sure the BIOS still sees the drive. You might also try creating an NTFS partition with a LiveCD (ubuntu livecd will need the ntfsprogs package for that).

Also, what version of Windows are you trying to install, and what kind of hard disk (SATA or PATA) and motherboard do you have?

Edit: I got distracted and 10 other people posted before I hit the post button. (sorry)

Okay... I'm pretty sure its a SATA disk. As for the motherboard, the best I can do is tell you it's a few months old, as is this laptop.

I'll go check the BIOS.

I'll update soon.

---

### Post by d8a on 2008-12-05
First of all, which Windows CD are you talking about? XP, Vista, 2000? I suppose you don't want to install any older Windows Version.

Second, there is no need to install Windows and shrink it's partition. Why would anyone want to do that? Just create a partition of the size you want for Windows and leave the rest unpartitioned. When you're finished installing Windows, use the unpartitioned space for Ubuntu.

Now about your main Problem: Is it possible that you have a SATA HDD and a Windows XP CD without the drivers for your SATA controller on it? (usually integrating SP2 or SP3 into the Windows XP does the trick)

Does Ubuntu find your HDD?

Reformatting your HDD to NTFS or FAT32 will not have any effect. The Windows (XP and probably 2000 and Vista too) setup either does find your HDD and offer's you to partition it, or it doesn't find it and that's it. It doesn't matter if there are any kinds of partitions on it.

---

### Post by Gonz_91 on 2008-12-05
> **d8a said:**
> First of all, which Windows CD are you talking about? XP, Vista, 2000? I suppose you don't want to install any older Windows Version.

Second, there is no need to install Windows and shrink it's partition. Why would anyone want to do that? Just create a partition of the size you want for Windows and leave the rest unpartitioned. When you're finished installing Windows, use the unpartitioned space for Ubuntu.

Now about your main Problem: Is it possible that you have a SATA HDD and a Windows XP CD without the drivers for your SATA controller on it? (usually integrating SP2 or SP3 into the Windows XP does the trick)

Does Ubuntu find your HDD?

Reformatting your HDD to NTFS or FAT32 will not have any effect. The Windows (XP and probably 2000 and Vista too) setup either does find your HDD and offer's you to partition it, or it doesn't find it and that's it. It doesn't matter if there are any kinds of partitions on it.

Okay, so how do I integrate SP3 into an XP CD?


Also, about the disk, that's what I was thinking to myself: it either finds it or not. Yes, Ubuntu live CD (USB in fact) finds it.

---

### Post by d8a on 2008-12-05
> **Gonz_91 said:**
> Okay, so how do I integrate SP3 into an XP CD?

A quick google search lead me to: 

[http://www.howtohaven.com/system/slipstream-xp-service-pack-3.shtml](http://www.howtohaven.com/system/slipstream-xp-service-pack-3.shtml)

Alternatively you can insert a floppy with your SATA drivers on it during setup when asked to press F6 for additional drivers. But i doubt your laptop has a floppy drive ...

---

### Post by Gonz_91 on 2008-12-05
> **d8a said:**
> A quick google search lead me to: 

[http://www.howtohaven.com/system/slipstream-xp-service-pack-3.shtml](http://www.howtohaven.com/system/slipstream-xp-service-pack-3.shtml)

Alternatively you can insert a floppy with your SATA drivers on it during setup when asked to press F6 for additional drivers. But i doubt your laptop has a floppy drive ...


Thank you very very much!

For now, I will bookmark all this, and go to sleep (it's getting kinda late here). First thing tomorrow I'll go fiddle with my Vista box and get that XP disc up and runnin'.


Thank you all, and good night!


(PS: I did not forget to mark the thread as SOLVED. I intend to do that tomorrow, after the disc recognizes my HDD)

---

