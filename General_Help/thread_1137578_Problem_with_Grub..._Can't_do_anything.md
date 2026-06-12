---
title: "Problem with Grub... Can't do anything"
date: 2009-04-25
forum: General Help
---

### Post by Alienwarek on 2009-04-25
I need some help... something happened and when I start my laptop my GRUB loader goes right to this

[ Minimal BASH-like line editing is supported. For
the first word, TAB lists possible command
completions. Anywhere else TAB lists the possible
completions of a device/filename. ]

grub>

so I can't go to windows or ubuntu... I've tried reinstalling grub, I've hit ESC and no I'm not hitting C... 
Can anyone help me?? right now I'm running ubuntu off the LIVE CD...

---

### Post by dcstar on 2009-04-25
> **Alienwarek said:**
> I need some help... something happened and when I start my laptop my GRUB loader goes right to this

[ Minimal BASH-like line editing is supported. For
the first word, TAB lists possible command
completions. Anywhere else TAB lists the possible
completions of a device/filename. ]

grub>

so I can't go to windows or ubuntu... I've tried reinstalling grub, I've hit ESC and no I'm not hitting C... 
Can anyone help me?? right now I'm running ubuntu off the LIVE CD...

Use the Live CD's Partition Editor to do a "Check" on your partitions.

---

### Post by Alienwarek on 2009-04-25
It won't let me do a "check" on my ubuntu partition :(

---

### Post by oldos2er on 2009-04-25
Make sure the partitions are not mounted.

---

### Post by Alienwarek on 2009-04-25
ok now it will let me check but it's recommending i backup valuable data before proceeding... I've tried to back up all my data but can't cause i get this "The folder "folder/file name" cannot be handled because you do not have permissions to read it" how can I fix that???

---

### Post by oldos2er on 2009-04-25
While you're running the LiveCD, can you open a terminal (Applications, Accessories, Terminal), and copy and paste the output from this command here?
```
sudo fdisk -l
```

---

### Post by Alienwarek on 2009-04-28
yeah... it comes up with this:

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb5c8be18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7295    58597056   83  Linux
/dev/sda2            7296        7357      498015   82  Linux swap / solaris
/dev/sda3   *        7358       14592    58115137+   7  HPFS/NTFS 

---

