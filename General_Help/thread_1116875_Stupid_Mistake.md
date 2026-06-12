---
title: "Stupid Mistake"
date: 2009-04-05
forum: General Help
---

### Post by handyman on 2009-04-05
I made a rather stupid mistake, I attempted to make one of my drives mount automaticlly at boot and did it the wrong way. 
I right clicked on the drive icon on the desk top then clicked properties, then drive, then settings. In the box marked "Enter Mountpoint" I put "/mnt/Data" (Data being the drive label) and in the box marked "Filesystem" I put ntfs. 
Now the drive cannot be mounted, I get the error message "mount_point cannot contain the following characters: newline, G_DIR_SEPARATOR (usually /) 
When I run GParted it shows "Partition dev sdb1...Filesystem unknown" 

Can anyone tell me how to correct this?

---

### Post by taurus on 2009-04-05
Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by handyman on 2009-04-05
Here is the output from sudo fdisk -l:

Disk /dev/sda: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x415ee81a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        2495    20033055    f  W95 Ext'd (LBA)
/dev/sda5   *           2        2495    20033023+   7  HPFS/NTFS

Disk /dev/sdb: 20.4 GB, 20404371456 bytes
255 heads, 63 sectors/track, 2480 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf8019347

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1          13      104391    6  FAT16
/dev/sdb2              14        2480    19816177+   f  W95 Ext'd (LBA)
/dev/sdb5              14        2480    19816146    7  HPFS/NTFS

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa622a622

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1275    10241406    7  HPFS/NTFS
/dev/sdc2            1276        2248     7815622+  83  Linux
/dev/sdc3            2249        2735     3911827+   f  W95 Ext'd (LBA)
/dev/sdc4            2736        4865    17109225    7  HPFS/NTFS
/dev/sdc5            2249        2613     2931831   83  Linux
/dev/sdc6            2614        2735      979933+  82  Linux swap / Solaris
bill@PC-1:~$ 

From sudo blkid:

bill@PC-1:~$ sudo blkid
/dev/sda5: UUID="BE98ADEA98ADA0FF" LABEL="USB-Drive" TYPE="ntfs" 
/dev/sdb5: UUID="F00C04C00C048436" LABEL="Data" TYPE="ntfs" 
/dev/sdc5: UUID="17b8308b-8963-4ced-a93d-25189e915b5c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc1: UUID="04C82E1FC82E0F8A" TYPE="ntfs" 
/dev/sdc2: UUID="53047f27-6d18-498f-a789-2177e3b6a649" TYPE="ext3" 
/dev/sdc4: UUID="3FF1EA3420356F32" LABEL="My-Disk" TYPE="ntfs" 
/dev/sdc6: TYPE="swap" UUID="745eec73-cf5f-49f1-aad2-0b747f18acc4" 
bill@PC-1:~$ 

From cat /etc/fstab

bill@PC-1:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=53047f27-6d18-498f-a789-2177e3b6a649 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=17b8308b-8963-4ced-a93d-25189e915b5c /home           ext3    relatime        0       2
# /dev/sda6
UUID=745eec73-cf5f-49f1-aad2-0b747f18acc4 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
bill@PC-1:~$ 

and from df -h

bill@PC-1:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc2             7.4G  3.4G  3.7G  49% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  216K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  104K  501M   1% /dev/shm
lrm                   501M  2.0M  499M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdc5             2.8G  947M  1.7G  36% /home
/dev/sda5              20G   11G  8.2G  58% /media/USB-Drive
bill@PC-1:~$ 

Hope this helps figure out how to fix.

Regards, Bill

---

### Post by taurus on 2009-04-05
/dev/sdb1 is fat16 filesystem, not ntfs.  If you want to have it mounted automatically each time you boot Ubuntu, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sdb1   /mnt/Data   vfat   iocharset=utf8,umask=000  0  0
```

Save it and exit gedit editing window.  Now, create a new mount point (if you haven't already) and mount it.

```
sudo mkdir /mnt/Data
sudo mount -a 
df -h
```

p.s.  Do you have anything on /dev/sdb1?  You can use gparted to reformat it if you can't mount it right now.

---

### Post by handyman on 2009-04-05
Thanks taurus, I did as you suggested and here is the output I got:

bill@PC-1:~$ sudo mkdir /mnt/Data
bill@PC-1:~$ sudo mount -a 
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

bill@PC-1:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc2             7.4G  3.4G  3.7G  49% /
tmpfs                 501M     0  501M   0% /lib/init/rw
varrun                501M  216K  501M   1% /var/run
varlock               501M     0  501M   0% /var/lock
udev                  501M  2.8M  498M   1% /dev
tmpfs                 501M  104K  501M   1% /dev/shm
lrm                   501M  2.0M  499M   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sdc5             2.8G  947M  1.7G  36% /home
/dev/sda5              20G   11G  8.2G  58% /media/USB-Drive
bill@PC-1:~$ 


What did I do wrong?

Thanks, Bill

PS I hope I didn't mislead you but the disks I cannot mount are actually /dev/sdb5 and /dev/sdc4 as listed in the output of the blkid command. Since I made the same error with both drives I figured the fix would be the same.

Bill

---

### Post by taurus on 2009-04-05
/dev/sdb5 & /dev/sdc4 are ntfs filesystem.

```
sudo mkdir /mnt/sdb5 /mnt/sdc4
sudo mount -t ntfs-3g /dev/sdb5 /mnt/sdb5
sudo mount -t ntfs-3g /dev/sdc4 /mnt/sdc4
df -h
```

---

### Post by Yashiro on 2009-04-05
Open gconf-editor.

system>storage>

Look there for the drive you added. Probably in the storage subkey.
Delete the erroneous data when you find it. Reboot, all sorted.

---

### Post by handyman on 2009-04-05
Thanks so much taurus, I have my drives back! Thank you too Yashiro although I was not able to figure out the fix your way. Taurus could you tell me what to add to fstab to mount these dives at boot? It will not be the same info as for mounting a fat drive.
Thanks, Bill

---

### Post by Yashiro on 2009-04-05
When you add mount points the way you did they're stored in the Gnome registry. It's somewhat like the windows registry.

The keys I mentioned hold the data that you entered via the gui.
So deleting the rubbish data from there corrects your mistake.

---

### Post by taurus on 2009-04-05
If you want to have those two ntfs partitions mounted automatically through /etc/fstab, then add these two lines to the end of it.

```

/dev/sdb5   /mnt/sdb5   ntfs-3g   defaults,locale=**en_US**.UTF-8   0   0
/dev/sdc4   /mnt/sdc4   ntfs-3g   defaults,locale=**en_US**.UTF-8   0   0

```
Save it and reboot.

---

