---
title: "Problem with Dual Boot"
date: 2009-01-30
forum: General Help
---

### Post by DavidSingleton on 2009-01-30
I'm having issues with my dual OS laptop here.  Grub doesn't see my windows install.  I can see my boot.ini file in my second partition from ubuntu, but I can't get it to boot into windows.  Here is what my boot.ini file shows in my windows partition:
```

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


```

Can anyone give me a hand with this?

---

### Post by bumanie on 2009-01-30
Can you post the output from terminal of > sudo fdisk -lI suspect the partitioning has got boot.ini and the windows partition out of sync.

---

### Post by Pidgin on 2009-01-30
In the GRUB menu, press C to enter the command-line interface. Then try these commands:
```
root (hd0,1)
chainloader +1
boot
```
It failing, change "[FONT="Monospace"](hd0,[COLOR="Red"]**1**[/COLOR])[/FONT]" and have some trials. If succeeding, you can edit your [FONT="Monospace"]menu.lst[/FONT].

---

### Post by DavidSingleton on 2009-01-30
output of fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02f702f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10437    83835171    7  HPFS/NTFS
/dev/sda2           10438       18241    62685630   83  Linux
/dev/sda3           18242       19457     9767520   82  Linux swap / Solaris

```

---

### Post by Pidgin on 2009-01-30
> **DavidSingleton said:**
> output of fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02f702f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10437    83835171    7  HPFS/NTFS
/dev/sda2           10438       18241    62685630   83  Linux
/dev/sda3           18242       19457     9767520   82  Linux swap / Solaris

```

Since the first partition is your Windows partition, I think the following commands would boot your Windows:
```
root (hd0,0)
chainloader +1
boot
```

---

### Post by DavidSingleton on 2009-02-02
Terrific, it worked.  Now if i can just figure out how to get it to appear in my grub menu i'll be set.  Thank both of you for your help

---

### Post by Pidgin on 2009-02-04
Press Alt+F2 and enter:
```
gksudo gedit /boot/grub/menu.lst
```
At the end of that file, add:
```
title Windows
root (hd0,0)
chainloader +1
```
The title can be anything you like. And it is not necessary to add the command [FONT="Monospace"]**boot**[/FONT].
Save and reboot.

---

