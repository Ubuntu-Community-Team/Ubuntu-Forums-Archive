---
title: "[SOLVED] trying to restore /home dir"
date: 2008-12-22
forum: General Help
---

### Post by DAllenSmith on 2008-12-22
recently I reinstalled ubuntu and figured it would be no problem because i had my /home set up on another partition. well all my data is still on that partition when it is mounted but i am completely stumped as to how I am supposed to restore that partition as my /home can anyone help me? thank you in advance

---

### Post by taurus on 2008-12-22
When you reinstalled Ubuntu, you should have mount that partition to /home but should not format it.  That's probably the easiest way. 

Otherwise, you need to edit /etc/fstab and add an entry in there for your /home.

---

### Post by DAllenSmith on 2008-12-22
> **taurus said:**
> When you reinstalled Ubuntu, you should have mount that partition to /home but should not format it.  That's probably the easiest way. 

Otherwise, you need to edit /etc/fstab and add an entry in there for your /home.

yes i have tried editing fstab with something i found but it did not work could u tell me what i need to put in there, please?
 

```
das@daslap:~$ sudo fdisk -l
[sudo] password for das: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002ddcc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4191    33664176   83  Linux
/dev/sda2            4192       19457   122624145    5  Extended
/dev/sda5            4378       19457   121130068+  83  Linux
/dev/sda6            4192        4377     1493982   82  Linux swap / Solaris

Partition table entries are not in disk order
das@daslap:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=fa8fb163-cf22-468f-9b05-50e244f7b2e0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=06978e7c-7dfb-4fd6-8712-d0cf2ea8a225 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda2 /home ext3 nodev,nosuid 0 2
das@daslap:~$ 

```

---

### Post by dcstar on 2008-12-22
> **DAllenSmith said:**
> 
........
das@daslap:~$ cat /etc/fstab
.......
/dev/sda2 /home ext3 nodev,nosuid 0 2

Try:

```
/dev/sda2 /home ext3 rw,errors=remount-ro,nodiratime,noatime 0 2
```

---

### Post by taurus on 2008-12-22
Replace this line in /etc/fstab

```
/dev/sda2 /home ext3 nodev,nosuid 0 2
```
with this one since /dev/sda5 is where /home is.

```
/dev/sda5   /home   ext3   defaults   0   2
```
Save it and reboot.

p.s.  /dev/sda2 is just an extended partition.

---

### Post by DAllenSmith on 2008-12-22
> **taurus said:**
> Replace this line in /etc/fstab

```
/dev/sda2 /home ext3 nodev,nosuid 0 2
```
with this one since /dev/sda5 is where /home is.

```
/dev/sda5   /home   ext3   defaults   0   2
```
Save it and reboot.

p.s.  /dev/sda2 is just an extended partition.

Thank you Taurus, your solution worked perfectly and you have saved me much headache, it was as simple as changing it from sda2 to sda5 i shouldve tried that:guitar:

---

### Post by Barriehie on 2008-12-23
I to have my /home on a different drive and I keep an actual printout of my fstab; that is commented to let me know which partition goes to what.  Kind of an un-losable backup... :)

Barrie

Edit: Also my /boot/grub/menu.lst

---

