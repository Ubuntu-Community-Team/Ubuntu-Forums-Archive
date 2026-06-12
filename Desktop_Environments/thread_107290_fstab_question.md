---
title: "fstab question"
date: 2005-12-22
forum: Desktop Environments
---

### Post by Pete051 on 2005-12-22
When I installed breezy I used reiserfs for / and /home with a small (30MB) /boot partition using ext2. Now on hoary I used the same configuration but with ext3 for / and /home. The thing is it used to run fsck every 30 or so boots now it doesn't run fsck at all, is this liable to be a future problem? fstab has hda1 as pass 2 (boot) and hda3 (/) as pass 1 and hda4 (home) as pass 2, do I have a problem here or is this normal?
Thanks
Pete

---

### Post by antidrugue on 2005-12-22
As ext2 is not a journaling file system, it runs fsck 30 reboots or at a given time interval (which I don't remember). Ext3 is a proper journaling file system, so it is of no use to run fsck periodically.

At least this what I understand.

Personally I only use reiserFS.

Though it seems that ext3 is [ the most reliable of them all]("http://linuxmafia.com/faq/Filesystems/reiserfs.html").

---

### Post by dcstar on 2005-12-22
[QUOTE=antidrugue]As ext2 is not a journaling file system, it runs fsck 30 reboots or at a given time interval (which I don't remember). Ext3 is a proper journaling file system, so it is of no use to run fsck periodically.

At least this what I understand.
.......[/QUOTE]
My "/" filesystem is ext3, and it gets the fsck treatment every 30 reboots.

---

### Post by antidrugue on 2005-12-22
[LEFT][quote=dcstar]My "/" filesystem is ext3, and it gets the fsck treatment every 30 reboots.[/quote]

Hehe, what do you know... I wasn't sure of that anyway. 


[LEFT]So how do you know it won't, "**Pete051". Have you already rebooted 30 times?**

It's unlikely that your filesystem is broken...

What does 
```

cat /etc/fstab

```

and 
```

sudo fdisk -l

```

say?
[/LEFT]
[/LEFT]

---

