---
title: "boot problems with GRUB"
date: 2016-04-11
forum: Fedora/RedHat and derivatives
---

### Post by folarin2 on 2016-04-11
Hi forum,

I'm unable to boot my system, when I get a "grub>" prompt and do an "ls" I can see:

(hd0) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos1)

and when I enter "ls /", I see a big list of kernels, system map etc too big to type out, but this is my kernel images and so on. According to online docs, I should see my root directory, but instead I see the contents of boot directory. 

edited to add: Only  (hd0,msdos1) can be seen, file system is not detected for the others but in (hd0,msdos1) I only see kernel images etc.


I think the problem is down to a maxed-out /boot directory because for some reason new kernels were not cycling (overwriting the third oldest kernel) so it just filled up the directory and now I can't start. However because I am using LVM and have most directories on an SSD drive, with /var. /swap and /home on the spin-disk... something has gone wrong and my system does not look like online documentation expects, most worryingly... I see the contents of boot when I do a "ls /", rather than root.

Any advise really appreciated, my laptop has an externel DVD drive and a ubuntu install disk is not detected when I try to boot from disk (I just get lots of whirring noises then it gives up, leaving the ThinkPad splash-screen in place, so no solutions available via Ubuntu DVD)

---

### Post by folarin2 on 2016-04-11
By the way, when I enter "set" on the "grub>" prompt,  I see "prefix=(hd0,msdos1)/grub" in the resulting list of settings, with "root=hd0,msdos1", hope that's useful info.

---

### Post by folarin2 on 2016-04-11
I have tried to use the boot repair tool to fix this, still getting a Kernel Panic on attempting to boot. I have a pastebin of my config however:

---

### Post by folarin2 on 2016-04-11
Hi forum, I have made a thread in Desktop Environments describing my problem, my 3rd post includes a pastebin taken by the Boot Repair tool showing my configs, any assistance or suggestions appreciated!

[http://ubuntuforums.org/showthread.php?t=2320174](http://ubuntuforums.org/showthread.php?t=2320174)

---

### Post by bapoumba on 2016-04-11
Threads merged (and moved to General Help).
Please do not start multiple threads on the same subject, it makes them difficult to follow, thanks.

---

### Post by oldfred on 2016-04-11
Since Centos with xfs & LVM, moved to Other Linux.

Boot-Repair cannot fix systems as complex as yours. It will offer to mount a /boot and mounts LVM, but will not add in all the other separate system partitions which may be needed to repair. You may have to chroot into system to repair and be sure to separately mount those partitions.

Do not know LVM, Centos or xfs.

Normally would suggest fsck to repair partitions but fsck is only for the ext2, ext3 & ext4 family of formats. You may need the equivalent for xfs.
And then run Boot-Repair to chroot into system and houseclean kernels. But with your separate partitions for / (root) folders, you have to chroot.

---

### Post by folarin2 on 2016-04-22
> **oldfred said:**
> Since Centos with xfs & LVM, moved to Other Linux.

Boot-Repair cannot fix systems as complex as yours. It will offer to mount a /boot and mounts LVM, but will not add in all the other separate system partitions which may be needed to repair. You may have to chroot into system to repair and be sure to separately mount those partitions.

Do not know LVM, Centos or xfs.

Normally would suggest fsck to repair partitions but fsck is only for the ext2, ext3 & ext4 family of formats. You may need the equivalent for xfs.
And then run Boot-Repair to chroot into system and houseclean kernels. But with your separate partitions for / (root) folders, you have to chroot.

Actually I never said I was running Centos, I'm not running Centos despite the partition names. If I was running Centos I would have started the thread over on a Centos forum. I did say that I was trying to install from a Ubuntu install disk didn't I, it's very difficult to install Centos using a Ubuntu install disk I think. My usual approach to installing Centos is to use a Centos install disk. 

In any case I have now resolved this issue, so please feel free to close the thread.

---

