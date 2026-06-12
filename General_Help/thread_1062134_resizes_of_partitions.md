---
title: "resizes of partitions"
date: 2009-02-06
forum: General Help
---

### Post by lulumara on 2009-02-06
I did finally was able  open the reboot  to Parted magic which allowed me to resize hard drive but when I resized it the 160Gb to  equal amount of 80Gb (first of all I did some unmount and mount  which can figure it out what that means looks like my hard drive is lock so I had to unmount). Then why there's like a interface or desktop when I used the parted magic , that really is? It's like a Ubuntu format of desktop or interface. And I reboot to ubuntu , at my hard drive looks like I cannot see the other half of my hard drive oh sorry I forgot to tell you that I had two Hard drive both the same size of 160Gb(One for Window XP and one for Ubuntu). When I go Ubuntu there's only 7.5Gb of free space and 2.5Gb occupied spaces,the other 70Gb that's remaining  I can see it but the other half is gone? Where did I go wrong?Any Idea?Thanks in advanced. But when I'm in Parted magic interface I can see that half as logical partition.

---

### Post by jerome1232 on 2009-02-06
Lets see what your partitions look like and what disks you have currently mounted for a start

to run these commands click Applications-Accessories-Terminal

To copy/paste in a terminal use ctrl+shift+c/v

For readabilty reasons post the output between code tags like this

[noparse]```
 output here 
```[/noparse]
```
sudo fdisk -lu
mount
```

---

### Post by lulumara on 2009-02-06
Can't do it now cause I'm on the office tonight I will post my hard drive ,sorry.Is there any change that I can put another OS like a Open SuSE or Debian in  my logical drive?

---

### Post by lulumara on 2009-02-06
isk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x21832182

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   312560639   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc306c306

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           16065   312576704   156280320    f  W95 Ext'd (LBA)
/dev/sdb5           16128   149420564    74702218+   7  HPFS/NTFS
/dev/sdb6       149420628   312576704    81578038+  83  Linux
jaime@ubuntu:~$

---

