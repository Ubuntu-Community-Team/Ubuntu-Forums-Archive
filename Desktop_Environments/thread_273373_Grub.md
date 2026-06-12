---
title: "Grub"
date: 2006-10-07
forum: Desktop Environments
---

### Post by MHlavsa on 2006-10-07
Background story:

I have a Ubuntu/XP duel boot PC
I remove XP and put on Vista[INDENT](Erases GRUB, I anticipated that, so made a "Super GRUB Disc"[/INDENT]

Problem:

I run the "'Super' GRUB Disc", go through to "Restore GRUB on MBR", and the CD dies... and computer reboots. :evil: 

Now I've been trying to get GRUB back from within the Live CD, and nothing is working.  I've looked at several sites telling me what to do and I can't get anything to work.

If this helps:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9065    72813568    7  HPFS/NTFS
/dev/sda2            9066       19321    82381320   83  Linux
/dev/sda3           19322       19452     1052257+  82  Linux swap / Solaris

```

I REALLY need help getting GRUB back.  I use Ubuntu as my primary OS for the computer, and want to get back into that.  Vista I'm not concerned about adding to GRUB yet.  I'd like to, but it's not a priority right now.  I'm way past what I understand about this, so if anyone can help me (the more specific the better... lines of code to enter would be best) that'd rock.  ](*,)

---

### Post by catlett on 2006-10-08
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) as long as your ubuntu partition wasn't touched during the removal/install of xp/vista, this will restore grub.

---

### Post by MHlavsa on 2006-10-08
That did it.  I had run that exactly the night before and it didn't work, so after trying 5 other thinks I quit.  I don't know why but running again worked.  Oh well.. ](*,)

---

