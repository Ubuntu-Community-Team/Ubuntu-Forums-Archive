---
title: "How do I fix my partition table?"
date: 2009-04-30
forum: General Help
---

### Post by Hawk__0 on 2009-04-30
I read a thread on almost the same topic but it's way over my head.  How do I fix this problem?

```
ubuntu@ubuntu:~$ sudo fdisk -l
**omitting empty partition (5)**

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          ** 1        9726 **   78124063+   5  Extended
/dev/sda2            **9325        9726**     3229033+  82  Linux swap / Solaris
/dev/sda5               **1        5241**    42098238   83  Linux
/dev/sda6            **5242        9324**    32796666    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$ 

```

I'm trying to SAVE my ubuntu partition while installing windows 7 on a different one but it won't install.  So I tried to format the partition (/dev/sda6 I guess..) with windows XP, which worked, but when I went to proceed with the install it said I can't do it because I have to overwrite a partition that is above it (my ubuntu partition I'm thinking it was talking about).

---

### Post by Hawk__0 on 2009-04-30
NOTE: this is a duplicate post because apparently I posted it in an area that is "read only" =\

I read a thread on almost the same topic but it's way over my head.  How do I fix this problem?

```
ubuntu@ubuntu:~$ sudo fdisk -l
**omitting empty partition (5)**

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          ** 1        9726 **   78124063+   5  Extended
/dev/sda2            **9325        9726**     3229033+  82  Linux swap / Solaris
/dev/sda5               **1        5241**    42098238   83  Linux
/dev/sda6            **5242        9324**    32796666    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$ 

```

I'm trying to SAVE my ubuntu partition while installing windows 7 on a different one but it won't install.  So I tried to format the partition (/dev/sda6 I guess..) with windows XP, which worked, but when I went to proceed with the install it said I can't do it because I have to overwrite a partition that is above it (my ubuntu partition I'm thinking it was talking about).

---

### Post by taurus on 2009-04-30
Does windows allow you to install it on a logical partition?

---

### Post by Hawk__0 on 2009-04-30
It doesn't let me install it.  It tells me it needs to install on a partition "one above" (which is my ubuntu one)

---

### Post by taurus on 2009-04-30
You can either resize your harddrive, making room for another primary partition so you can install windows on it, or redo the whole thing over again, windows and Ubuntu.

---

### Post by Niniel on 2009-04-30
You don't need to "fix" your partition table, but you may need to repartition.
If I interpret your fdisk output correctly, you have a bit of a weird setup there - an extended partition with Linux and Windows, and a primary partition with the Linux swap file.
Btw, "omitting empty partition (5)"? 
Maybe you can post a screenshot of GPartEd showing your sda? And is that your only disk?
Anyway, Windows 7 may be asking for a primary partition to install to. Can you find out if that's the case?

---

### Post by Hawk__0 on 2009-04-30
Yup that's what I'm doing..... backing up my home folder on a network drive and preparing for an install.... fail.  Windows 7 first, of course.

How is Jaunty?  I'm using hardy right now... and I think I'll install Jaunty this time

---

### Post by ajgreeny on 2009-04-30
> How is Jaunty?  I'm using hardy right now... and I think I'll install Jaunty this time
It will depend on your hardware of course, but on my machine, 4 year old Sempron 2400+, ati 9200SE graphics, 1GB ram, it is absolutely great, the best Ubuntu yet, with no real problems at all.  I've become fairly adept at adding all the multimedia codecs and apps I want and could need, and they all seem to work brilliantly.  I admit I have never yet done a version upgrade, always a clean install, and I think a lot of people's problems stem from upgrades rather than clean installs, so that is what I would suggest.

---

### Post by caljohnsmith on 2009-04-30
> **Hawk__0 said:**
> I read a thread on almost the same topic but it's way over my head.  How do I fix this problem?

```
ubuntu@ubuntu:~$ sudo fdisk -l
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           [COLOR="Red"]1        9726[/COLOR]    78124063+   5  Extended
/dev/sda2            [COLOR="Red"]9325        9726[/COLOR]     3229033+  82  Linux swap / Solaris
/dev/sda5               1        5241    42098238   83  Linux
/dev/sda6            5242        9324    32796666    e  W95 FAT16 (LBA)
ubuntu@ubuntu:~$ 

```

Anytime fdisk says "omitting empty partition (X)", that's unfortunately a sure sign that your partition table is corrupt. In your case, the sda2 Linux partition is inside your sda1 extended partition (you can tell from the start/stop points highlighted in red above); therefore sda2 should be a logical partition, or sda1 should be resized so it doesn't include sda2 inside of it. The other issue is that you are trying to install Windows to sda6, which is a logical partition; Windows (being as flexible as it is :rolleyes:) won't let you install to a logical partition unless there is a primary NTFS/FAT partition available where Windows can put its boot files. 

I would recommend converting sda5 and sda6 into primary partitions, and then making the sda2 swap partition a logical partition. Then you shouldn't have any problems installing Windows. If you would like help doing that, how about posting the following:
```
sudo fdisk -lu
sudo sfdisk -d
```
And we can work from there if you want. :)

John

P.S. Your other thread that you started in the Beginner Forum was not "read only", so please only start one thread for each subject/problem out of consideration of those who try to help you. Thanks!

---

