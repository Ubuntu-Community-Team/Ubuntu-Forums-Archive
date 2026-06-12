---
title: "[SOLVED] grub does not show one of my operating systems"
date: 2009-01-10
forum: General Help
---

### Post by beattyml1 on 2009-01-10
I recently switched my grub boot loader from one grub install to another, and the new one does not show all the operating systems like the previous, however I want to keep this grub install as it is the one associated with my current main OS any ideas on how to add an OS to the grub boot list

---

### Post by unutbu on 2009-01-10
Type 
```

sudo fdisk -l
```

You will see something like this:
```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2          112455    10602899     5245222+   b  W95 FAT32
/dev/sda3   *    10602900    51568649    20482875   83  Linux
/dev/sda4        51568650   625137344   286784347+   5  Extended
/dev/sda5        51568713    92534399    20482843+  83  Linux
/dev/sda6        92534463   356787584   132126561   83  Linux
/dev/sda7       356787648   621040769   132126561   83  Linux
/dev/sda8       621040833   625137344     2048256   82  Linux swap / Solaris

```
Find the Linux partition associated with your previous operating system. Mount that partition:
```

sudo mount  [COLOR="Red"]/dev/sda5[/COLOR]   /mnt
```
[COLOR="Red"]Change /dev/sda5 to the correct name for your partition.[/COLOR]

```

gedit /mnt/boot/grub/menu.lst
```

Around 2/3 of the way down through /mnt/boot/grub/menu.lst you will find stanzas like this:
```

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		e8c543ef-c9c3-47f6-82bc-d35b5ff8f615
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=e8c543ef-c9c3-47f6-82bc-d35b5ff8f615 ro quiet 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
```

Each stanza corresponds to one boot option in the GRUB menu.
Copy the stanzas you want into your current /boot/grub/menu.lst.

Use gksu to give you root privileges, so you can edit /boot/grub/menu.lst:
```

gksu gedit /boot/grub/menu.lst

```
Copy and paste the stanzas from /mnt/boot/grub/menu.lst into /boot/grub/menu.lst.

---

### Post by fooman on 2009-01-10
please post output from these 2 commands:

```
gedit /boot/grub/menu.lst
``````
sudo fdisk -l
```

edit:  too slow.

---

