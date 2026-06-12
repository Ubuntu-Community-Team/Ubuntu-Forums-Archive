---
title: "Grub boot problem  with Ubuntu 8.10 &amp; Win Xp"
date: 2009-05-29
forum: General Help
---

### Post by brecha on 2009-05-29
hi guys

im having problems with my grub..i have ubuntu 8.10 Kernel 2.6.27-13generic in a laptop toshiba satellite A105-S4064
and im having some issues with the grub or the boot sector because i have to restore the grub almost every time i turn on my laptop.

the problem start when i turn on my laptop and the grub just get viewed to the part it says .. Grub loading Stage 5.. Grub loading..
and the computer restart it self.. so i start my laptop with a Kubuntu live cd.. restore the Grub.. and its done and working fine.. but several times i turn on my laptop (cold start) i get the same problem

Possible reasons cheked

- Scanned my hard drive so find bad sectors -> OK none were find
- Gsmartcontrol - > to find another possible issues with the hard drive.... None were find (Everything was OK)


if anyone had this problem... or just almost the same.. i will appreciate the help

Thanks

---

### Post by lindsay7 on 2009-05-29
How are you restoring the grub menu?

---

### Post by brecha on 2009-05-29
> **lindsay7 said:**
> How are you restoring the grub menu?


#sudo grub
#root (hd0,1)
#setup (hd0)

Done!

---

### Post by lindsay7 on 2009-05-29
Try this, you may not be changing th grub menu on the hard drive just the cd.



See if this works for you. Type these commands in the terminal





Sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hdx)
quit

---

### Post by brecha on 2009-05-29
> **lindsay7 said:**
> Try this, you may not be changing th grub menu on the hard drive just the cd.



See if this works for you. Type these commands in the terminal





Sudo grub
find /boot/grub/stage1
(it will give a (hdx,y)
root (hdx,y)
setup (hdx)
quit

i`ve trying this way since my first time.. the thing is that i wrote it resumed..

but after..

#find /boot/grub/stage1   --> i get (hd0,1)
so i tried

root (hd0,1)
setup (hd0)
quit

after this process the grub get restored.. but after restart my laptop a couple of times.. i have to do the same grub restore.. again..!

---

### Post by nebileix on 2009-05-29
Any changes was made to menu.lst? By you or maybe scripts or "someone" else?

---

### Post by brecha on 2009-05-29
> **nebileix said:**
> Any changes was made to menu.lst? By you or maybe scripts or "someone" else?

nope..!

also i restore my menu.lst from my old backup

---

### Post by lindsay7 on 2009-05-29
You could update to 9.04 and see if that clears thing up.

type alt +f2 and type update-manager -d

Other then that I have no clue.

---

### Post by VMC on 2009-05-29
You stated in your first post that (I'm assuming) there are no grub error messages and that grub goes from stage 1.5 to rebooting. Is that correct.

Once you get grub booting again, give us the following.

```
sudo fdisk -l
cat /boot/grub/menu.lst
cat /etc/fstab
df -Th
```

PS: Is there some hidden storage file system?

---

### Post by brecha on 2009-05-29
no i dont have a hidden storage file system

> **VMC said:**
> You stated in your first post that (I'm assuming) there are no grub error messages and that grub goes from stage 1.5 to rebooting. Is that correct.

Once you get grub booting again, give us the following.

```
sudo fdisk -l
cat /boot/grub/menu.lst
cat /etc/fstab
df -Th
```

PS: Is there some hidden storage file system?


```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7baf7ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         249     2000061   82  Linux swap / Solaris
/dev/sda2             250        1494    10000462+  83  Linux
/dev/sda3   *        1495        6827    42837322+   7  HPFS/NTFS
/dev/sda4            6828       12160    42837322+   f  W95 Ext'd (LBA)
/dev/sda5            6828       12160    42837291    7  HPFS/NTFS

```



```
title		Ubuntu 8.10, kernel 2.6.27-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=d53b35d0-62ee-46ab-9e3c-d6b4837fc82b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=d53b35d0-62ee-46ab-9e3c-d6b4837fc82b ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-13-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-13-generic root=UUID=d53b35d0-62ee-46ab-9e3c-d6b4837fc82b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-13-generic
quiet

##title		Ubuntu 8.10, kernel 2.6.27-13-generic (recovery mode)
##root		(hd0,1)
##kernel		/boot/vmlinuz-2.6.27-13-generic root=UUID=d53b35d0-62ee-46ab-9e3c-d6b4837fc82b ro  single
#initrd		/boot/initrd.img-2.6.27-13-generic

#title		Ubuntu 8.10, kernel 2.6.27-7-generic
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d53b35d0-62ee-46ab-9e3c-d6b4837fc82b ro quiet splash 
#initrd		/boot/initrd.img-2.6.27-7-generic
#quiet

##title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
##root		(hd0,1)
##kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=d53b35d0-62ee-46ab-9e3c-d6b4837fc82b ro  single
##initrd		/boot/initrd.img-2.6.27-7-generic

##title		Ubuntu 8.10, kernel 2.6.24-21-generic
##root		(hd0,1)
##kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d53b35d0-62ee-46ab-9e3c-d6b4837fc82b ro quiet splash 
##initrd		/boot/initrd.img-2.6.24-21-generic
##quiet

##title		Ubuntu 8.10, kernel 2.6.24-21-generic (recovery mode)
##root		(hd0,1)
##kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=d53b35d0-62ee-46ab-9e3c-d6b4837fc82b ro  single
##initrd		/boot/initrd.img-2.6.24-21-generic

##title		Ubuntu 8.10, kernel 2.6.22-14-generic
##root		(hd0,1)
##kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d53b35d0-62ee-46ab-9e3c-d6b4837fc82b ro quiet splash 
##initrd		/boot/initrd.img-2.6.22-14-generic
##quiet

##title		Ubuntu 8.10, kernel 2.6.22-14-generic (recovery mode)
##root		(hd0,1)
##kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=d53b35d0-62ee-46ab-9e3c-d6b4837fc82b ro  single
##initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 8.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title           Microsoft Windows XP Professional
root            (hd0,2)
savedefault
makeactive
chainloader     +1

```


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=d53b35d0-62ee-46ab-9e3c-d6b4837fc82b /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda3
UUID=B2189B10189AD329 /media/sda3     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda5
UUID=BE58122B5811E347 /media/sda5     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=cadf4c3f-7733-40c0-9b6c-8644758e1249 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

```

```
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda2     ext3    9.4G  7.5G  1.5G  84% /
tmpfs        tmpfs    500M     0  500M   0% /lib/init/rw
varrun       tmpfs    500M  348K  500M   1% /var/run
varlock      tmpfs    500M     0  500M   0% /var/lock
udev         tmpfs    500M  2.7M  498M   1% /dev
tmpfs        tmpfs    500M  316K  500M   1% /dev/shm
lrm          tmpfs    500M  2.0M  498M   1% /lib/modules/2.6.27-14-generic/volatile
/dev/sda5  fuseblk     41G   39G  2.1G  95% /media/sda5
/dev/scd0  iso9660    695M  695M     0 100% /media/cdrom0

```

---

### Post by brecha on 2009-06-01
hey.. where everybody go ??.. im keep waiting.. :popcorn:

---

### Post by VMC on 2009-06-01
windows doesn't like to be anywhere except the first partition. Your setup is a bit odd. You have your swap as the first partition, but that shouldn't matter, just curious how you originally set up the hard drive:


title           Microsoft Windows XP Professional
root            (hd0,2)
savedefault
makeactive
chainloader     +1

Try using this to boot Windows
title Microsoft Windows XP Professional
root (hd0,2)
savedefault
map (hd0,0) (hd0,2)
map (hd0,2) (hd0,0)
makeactive
chainloader +1

---

### Post by brecha on 2009-06-02
why you suggest the map part ??

---

### Post by VMC on 2009-06-02
> **brecha said:**
> why you suggest the map part ??

Read this:
[http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html](http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html)

---

### Post by brecha on 2009-06-05
thanks dude.. i think the problem is solved.. i had restarted my laptop several times, and i dont get the grub restarting error..

Thanks ):P

any changes i let you know!

---

