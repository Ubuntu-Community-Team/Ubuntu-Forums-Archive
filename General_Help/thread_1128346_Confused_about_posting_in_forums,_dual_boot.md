---
title: "Confused about posting in forums, dual boot"
date: 2009-04-17
forum: General Help
---

### Post by crunchbangsucks on 2009-04-17
I was trying to post in the absolute beginners forum but I cant.
Does anyone know why this is?

Anyway my problem was that I was trying to dual boot (xp,ubuntu) and I followed the instructions on this page

[http://ubuntuforums.org/showthread.php?t=223031](http://ubuntuforums.org/showthread.php?t=223031)

At the end all it would do was boot up ubuntu and did not give me the option to boot windows.

Any help would be appreciated

---

### Post by cariboo on 2009-04-17
I would suggest you check to see if you still have a Windows partition, as you may have accidently over written it. To make sure could you open an Applications-->Accessories-->Terminal and type:

```
sudo fdisk -l
```

and paste the results in your next post.

Jim

---

### Post by crunchbangsucks on 2009-04-17
Sudo: fdisk: don@don-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03540353

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3022    24274183+  83  Linux
/dev/sda2            3023        4117     8795587+   5  Extended
/dev/sda3   *        4118        7575    27776385    7  HPFS/NTFS
/dev/sda4            7576        9729    17302005   83  Linux
/dev/sda5            3023        3421     3204936   82  Linux swap / Solaris
/dev/sda6            3422        4117     5590588+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9bdbf65f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60637   487066671   83  Linux
/dev/sdb2           60638       60801     1317330    5  Extended
/dev/sdb5           60638       60801     1317298+  82  Linux swap / Solaris
don@don-laptop:~$ 




was the response to your command

---

### Post by ajgreeny on 2009-04-17
It looks as if you still have windows installed on sda3, rather than the sda1 that I was expecting.  Nevermind, it's still on your computer, thank goodness.  However you do appear to have a rather complicated partition arrangement, with either more than one linux installation, or several partitions for the Ubuntu you installed, though I can't figure out why some are before your windows partition and some are after it.

OK, I've just looked at the thread you linked to, and now I see why you may have ended up with windows partition after linux on the disk, but it still does not explain why you have three partitions plus swap for your ubuntu.  Was this done on purpose, or by accident?

---

### Post by crunchbangsucks on 2009-04-17
it was my goal to have ubuntu, xp, and helix(to practice its contained software without having to carrry the disk)

sda1-ubuntu
sda2-extended

[INDENT]sda5-swap[/INDENT]

[INDENT]sda6-home[/INDENT]

sda3-xp
sda4-where helix would go

i installed ubuntu first and didnt think it mattered much where it all went on the disk as long as it had the required space.
does it matter?

is that a good enough explanation? does it make any more sense?

---

### Post by Iowan on 2009-04-17
> **crunchbangsucks said:**
> I was trying to post in the absolute beginners forum but I cant.
Does anyone know why this is?
 If you can post here, you *should* be able to post in Absolute Beginners... There is no qualification (aside from registration)  for *most* forums...

---

### Post by lisati on 2009-04-17
> **Iowan said:**
> If you can post here, you *should* be able to post in Absolute Beginners... There is no qualification (aside from registration)  for *most* forums...

There is an [archived section of Absoulute Beginners ]("http://ubuntuforums.org/forumdisplay.php?f=73")that doesn't accept new posts. The section of Absolute Beginners that DOES accept new posts is here: [http://ubuntuforums.org/forumdisplay.php?f=32](http://ubuntuforums.org/forumdisplay.php?f=32)

---

### Post by ajgreeny on 2009-04-17
> **crunchbangsucks said:**
> it was my goal to have ubuntu, xp, and helix(to practice its contained software without having to carrry the disk)

sda1-ubuntu
sda2-extended[INDENT]sda5-swap[/INDENT][INDENT]sda6-home[/INDENT]sda3-xp
sda4-where helix would go

i installed ubuntu first and didnt think it mattered much where it all went on the disk as long as it had the required space.
does it matter?

is that a good enough explanation? does it make any more sense?
Yes, I now understand and think that all that is needed is to add a stanza for windows to your /boot/grub/menu.lst

Try the following:-
```
# This entry manually added by user
# on /dev/sda3
title        Microsoft Windows XP
root        (hd0,2)
savedefault
makeactive
chainloader    +1
```I hope it works for you. Good luck.

---

