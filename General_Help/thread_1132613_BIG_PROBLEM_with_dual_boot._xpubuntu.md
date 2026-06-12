---
title: "BIG PROBLEM with dual boot. xp/ubuntu"
date: 2009-04-22
forum: General Help
---

### Post by miltk on 2009-04-22
I installed ubuntu on a second hd on my wife's computer. she runs xpHOME.

I can boot into ubuntu but not her xphome. the grub menu lists "nt/2000/xp" and "xp pro" as other OS's but not her xpHOME. Either option i try does NOT boot into windows, and loops back to the grub menu. She's gonna kill me.

Is there any way I can fix this from the ubuntu side?

---

### Post by James_Lochhead on 2009-04-22
**NOTE: Please read the second post first before doing this.**

Yes. The menu is just a text file. Here are some instructions that might help you:

[LIST]
[*]Open a terminal (Applications > Accessories > Terminal).
[*]First lets make a backup of the file. Type the following in the terminal:

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

```

[*]Now lets edit the file in a text editor:

```

sudo gedit /boot/grub/menu.lst

``` 

[*]At the bottom of text editor window type:

```

title		Windows XP
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```
[/LIST]

---

### Post by James_Lochhead on 2009-04-22
Okay because (I assume) you are reasonably unexperienced I think it is a good idea to make sure everything is picture perfect before you do the first post and restart the computer.

Open a terminal (as above) and type

```

sudo fdisk -l

```

Post the output here.

---

### Post by miltk on 2009-04-22
fdisk: invalid option -- '1'

btw...i got  an error 21 when i tried gedit and rebooted. i thought i'd try that first instead of waiting for a reply.

---

### Post by Merk42 on 2009-04-22
> **miltk said:**
> fdisk: invalid option -- '1'

btw...i got  an error 21 when i tried gedit and rebooted. i thought i'd try that first instead of waiting for a reply.

L as in Linux, not 1 as in one

---

### Post by miltk on 2009-04-22
okay...
btw, when i tried to backup, i got 

cp: cannot stat `/boot/grub.menu.lst': No such file or directory

---

### Post by miltk on 2009-04-22
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8760b932

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         784     6297448+  12  Compaq diagnostics
/dev/sda2             785        9729    71850712+  44  Unknown

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa53615eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   42  SFS

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc30278c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        9327    74919096   83  Linux
/dev/sdc2            9328        9729     3229065    5  Extended
/dev/sdc5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdd: 40.0 GB, 40007761920 bytes
240 heads, 63 sectors/track, 5168 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x4f9b89dd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1        5168    39070048+   c  W95 FAT32 (LBA)

---

### Post by Merk42 on 2009-04-22
> **miltk said:**
> okay...
btw, when i tried to backup, i got 

cp: cannot stat `/boot/grub.menu.lst': No such file or directory

it's /boot/grub/menu.lst (a file called menu.lst in the folder grub which is in the folder boot)

also, try just opening up said file (it'll be read only) and copy/paste it in your reply

---

### Post by snowpine on 2009-04-22
> **miltk said:**
> okay...
btw, when i tried to backup, i got 

cp: cannot stat `/boot/grub.menu.lst': No such file or directory

Friendly advice, when someone gives you a terminal command, try copying and pasting it into the terminal. This will avoid the risk of typos. :)

It should be /boot/grub/menu.lst not /boot/grub.menu.lst. It is important to be 100% accurate with terminal commands.

---

### Post by miltk on 2009-04-22
okay, thanks  again.

after gedit, i  rebooted an i get fatal system error, and the computer shuts down.

---

### Post by chomptown on 2009-04-22
You might have better luck using super grub disk, as it can replace your menu.lst for you.  [Click Here]("http://www.supergrubdisk.org/") and create a boot disk, then boot off it.  Last time I tried to go to the official supergrubdisk site, it was having some problems, so you might want to try a [mirror]("http://supergrub.forjamari.linex.org/").

---

