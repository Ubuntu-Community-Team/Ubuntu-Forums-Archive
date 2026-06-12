---
title: "mount and readable hdd's"
date: 2022-04-22
forum: Desktop Environments
---

### Post by devdlp on 2022-04-22
Im on Kubuntu 20.04 right now and i have 3 hard drives. two ssd's and 1 hdd. but they wont show up in steam.
just the main one will.
how do i get steam to see or better yet mount  and make readable everytime i log into the desktop plz

---

### Post by devdlp on 2022-04-22
[FONT=monospace][COLOR=#54ff54]**chewy@chewy-MS-7850**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ cat /etc/fstab [/COLOR]
# /etc/fstab: static file system information. 
# 
# Use 'blkid' to print the universally unique identifier for a 
# device; this may be used with UUID= as a more robust way to name devices 
# that works even if disks are added and removed. See fstab(5). 
# 
# <file system> <mount point>   <type>  <options>       <dump>  <pass> 
# / was on /dev/sda5 during installation 
UUID=eddfca93-5f03-401a-90d2-b82fb47aa4f4 /               ext4    errors=remount-ro 0   
    1 
# /boot/efi was on /dev/sda1 during installation 
UUID=9566-96C3  /boot/efi       vfat    umask=0077      0       1 
/swapfile                                 none            swap    sw              0     
  0


[/FONT]

---

### Post by devdlp on 2022-04-22
[FONT=monospace]There are no filesystems which you are allowed to mount or unmount.
Contact your administrator.

it says this when i try to launch disk management
[/FONT]

---

### Post by #&amp;thj^% on 2022-04-22
So to have them mounted on every boot:
example for mine:
```
/etc/fstab
# <file system> <mount point> <type> <options> <dump> <pass>

UUID=63BD-EAAC	/boot/efi	vfat	umask=0077	0	2
UUID=e11cf870-f82e-4b41-9ad3-a99e93667218	/	ext4	defaults,noatime	0	1
/swapfile	swap	swap	defaults,noatime	0	0
tmpfs	/tmp	tmpfs	defaults,noatime,mode=1777	0	0
UUID=be93f3dc-cd54-4321-9a9f-558c1317fc44	/media/data	ext4	defaults	0	0
/swapfile	none	swap	sw	0	0

```
this is the only one I want  mounted> "UUID=be93f3dc-cd54-4321-9a9f-558c1317fc44	/media/data	ext4	defaults	0	0"
to get what is needed for a placement in fstab i use:
```
sudo blkid

```
if you need more just ask

---

### Post by devdlp on 2022-04-22
Fixed!!! looks like i already posted a tread with that same problem and did
sudo chown -R $USER:$USER /mountponit and its all well and good now

---

