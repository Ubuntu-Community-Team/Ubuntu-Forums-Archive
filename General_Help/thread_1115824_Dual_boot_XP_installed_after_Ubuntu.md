---
title: "Dual boot: XP installed after Ubuntu"
date: 2009-04-04
forum: General Help
---

### Post by kernel89 on 2009-04-04
How should I edit my grub menu.lst in order to successfully boot between XP and Ubuntu?

I tried:

```

title Windows XP
root (hd1,0)
makeactive
chainloader +1 

&

title Windows XP
root (hd0,)
makeactive
chainloader +1 

&

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

```

And I either get Error 13 or Error 21

This is after doing: fdisk -lu

```

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0d710d71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     5670944     2835441    f  W95 Ext'd (LBA)
/dev/sda2   *     5670945   327806324   161067690   83  Linux
/dev/sda3       327806325   390700799    31447237+   7  HPFS/NTFS
/dev/sda5             126     5670944     2835409+  82  Linux swap / Solaris

```

---

### Post by kernel89 on 2009-04-04
Also whats the meaning of hd1,0 are they linked with the dev/sda numbers?

---

### Post by gollybegully on 2009-04-04
Try:

title Windows XP
root (hd0,1)
makeactive
chainloader +1

---

### Post by kernel89 on 2009-04-04
Yeah I tried that too, it was a typo on my first post.

---

### Post by ajgreeny on 2009-04-04
Which partition is your windows install?  It looks as if it is sda3 from your fdisk output, which in grub-speak is hd0,2 (grub starts from 0 (zero)).  I hope it's not sda1, as that is an extended partition, I think, and it is very difficult to boot windows from an extended partition.

If my first supposition is right, and if the previous posters suggestion is no good, try
title Windows XP
root (hd0,2)
makeactive
chainloader +1

---

### Post by kernel89 on 2009-04-04
> **ajgreeny said:**
> Which partition is your windows install?  It looks as if it is sda3 from your fdisk output, which in grub-speak is hd0,2 (grub starts from 0 (zero)).  I hope it's not sda1, as that is an extended partition, I think, and it is very difficult to boot windows from an extended partition.

If my first supposition is right, and if the previous posters suggestion is no good, try
title Windows XP
root (hd0,2)
makeactive
chainloader +1

Worked like a charm, thanks a lot! BTW, I realized my Windows drive has J:/ assigned instead of C:/ which makes the installation of drivers mighty complicated. Is there a way to change the partition letter, which Gparted maybe?

---

### Post by ajgreeny on 2009-04-04
> Worked like a charm, thanks a lot! BTW, I realized my Windows drive has J:/ assigned instead of C:/ which makes the installation of drivers mighty complicated. Is there a way to change the partition letter, which Gparted maybe?Sorry, but I have absolutely no idea how, or even if you can do this with anything at all.

---

### Post by revenant138 on 2009-04-04
Just to add on for anyone out there:

If you have a separate hdd, you need to remap it in menu.lst to get windows to think its on the first partition of the first drive.

For instance, I just installed windows on my 4th hard drive. To get it to work, my menu.lst entry is:

title           Windows XP
map             (hd0,0) (hd3,0)
map             (hd3,0) (hd0,0)
rootnoverify    (hd3,0)
makeactive
chainloader     +1

(To figure out its hd3, I did an fdisk -l to list the drives, and it shows up as sdd = 4th drive) 

You have to remap it, and use rootnoverify so it doesn't try to mount it.

On a side note, the hard drive was the only drive on the IDE cable and setup as slave (I had taken the master out) Windows installed fine, booted fine, but to get GRUB happy I had to switch it to master.

Hope this helps someone :)

---

