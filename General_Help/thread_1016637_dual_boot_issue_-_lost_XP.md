---
title: "dual boot issue - lost XP"
date: 2008-12-20
forum: General Help
---

### Post by giruzz on 2008-12-20
Hi Guys,

I recently updated my ubuntu and my partition with WinXp is gone.

```

title		Ubuntu 8.10, kernel 2.6.27-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=a8b24b7f-9fe9-47bd-9731-4418d94b9813 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-10-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.27-10-generic root=UUID=a8b24b7f-9fe9-47bd-9731-4418d94b9813 ro  single
initrd		/boot/initrd.img-2.6.27-10-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

```

Is my menu.lst and win XP is /dev/sda5

I have tried to type 

```
title		Windows XP
root		(hd0,5)
makeactive
chainloader+1
```

but it doesn't work...

anyone can help?

Thank you

Giruzz

---

### Post by lovelyvik293 on 2008-12-20
Please post the output of
```

sudo fdisk -l

```

---

### Post by giruzz on 2008-12-20
> **lovelyvik293 said:**
> Please post the output of
```

sudo fdisk -l

```

AS requested:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x322e322d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2167    17406396   83  Linux
/dev/sda2   *        2168        2550     3076447+  82  Linux swap / Solaris
/dev/sda3            2551        6741    33664207+   f  W95 Ext'd (LBA)
/dev/sda4            6742        7296     4458037+   7  HPFS/NTFS
/dev/sda5            2551        6741    33664176    7  HPFS/NTFS

---

### Post by TeXtonyx on 2008-12-20
Is my menu.lst and win XP is /dev/sda5

I have tried to type

Code:

title		Windows XP
root		(hd0,5)
makeactive
chainloader+1


-----------------------------

sda5 = (hd0,4)
The notation is one number less for the partition, sda*5*
for root in menu.lst, hd0 is first drive, 4 is fifth partition

The notation that you used is for sda6 = (hd0,5)

---

### Post by lovelyvik293 on 2008-12-20
If u have th windows installation on sda5 you have to use:-
```

title Windows XP
root (hd0,4)
makeactive
chainloader +1

```

---

### Post by giruzz on 2008-12-20
> **TeXtonyx said:**
> Is my menu.lst and win XP is /dev/sda5

I have tried to type

Code:

title		Windows XP
root		(hd0,5)
makeactive
chainloader+1

sda5 = (hd0,4)

-------------------------------------

The notation is one number less for the partition, sda*5*
for root in menu.lst, hd0 is first drive 4 is fifth partition

The notation that you used is for sda6

I have tried already..and it doesn't work...

giruzz

---

### Post by lovelyvik293 on 2008-12-20
@giruzz
use
```

title Windows XP
root (hd0,4)
makeactive
chainloader +1

```

---

### Post by giruzz on 2008-12-20
> **lovelyvik293 said:**
> @giruzz
use
```

title Windows XP
root (hd0,4)
makeactive
chainloader +1

```

Nope. Ivalid device..

giruzz

---

### Post by lovelyvik293 on 2008-12-20
If you have the windows in /dev/sda5 then this is the right entry.But i don't know why it's not working.

---

### Post by caljohnsmith on 2008-12-20
Giruzz, you are currently getting a Grub error because Grub can't make a logical partition "active", i.e. set the boot flag. Try removing the "makeactive" line in your menu.lst entry, and if that doesn't work to boot Windows, then how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

---

### Post by giruzz on 2008-12-20
> **caljohnsmith said:**
> Giruzz, you are currently getting a Grub error because Grub can't make a logical partition "active", i.e. set the boot flag. Try removing the "makeactive" line in your menu.lst entry, and if that doesn't work to boot Windows, then how about doing:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "boot_info_results.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post. That will help clarify your setup and what your problem might be.

Hi,
Actually..the solution was much simpler...
I'm an idiot...i was misspelling one word..and the system was returning an error..

Thank you all for the help!!

giruzz

---

### Post by TeXtonyx on 2008-12-20
chainloader+1
chainloader +1

---

