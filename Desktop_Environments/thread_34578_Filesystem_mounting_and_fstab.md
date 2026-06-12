---
title: "Filesystem mounting and fstab"
date: 2005-05-15
forum: Desktop Environments
---

### Post by himuraken on 2005-05-15
I have a couple filesystems that I would like to have mounted at boot time and would like these filesystems to be mounted in read and write mode for root and my own user. Obviously root has access when I run the mount command on a filesystem from the command line, but as stated above would like this to happen at boot. What are the proper steps for acheiving this? I have taken a look at /etc/fstab and it seems as simple as adding a mount entry to the list, but the permissions is where I get hung up at. Thank you.

---

### Post by Ali_Baba on 2005-05-15
Create a directory for your mount point and make your user as owner of that directory.Then write the fstab line with options rw.Then reboot,that has worked for 
me :) Im not sure if this works for fat partitions

---

### Post by RastaMahata on 2005-05-15
First, create mount points in /media (Folders). You should do this as root.
So, lets say you want to mount a fat32 filesystem. First, you should create a mount point. Lets say /media/fat32. So, you should:```
sudo mkdir /media/fat32
```Then, you should list all the hard drives mounted on your system. To do this, you must issue the fdisk command as root, as follows:```
sudo fdisk -l
```Here's my output, for example (In spanish)```
Disco /dev/hda: 40.0 GB, 40037760000 bytes
16 cabezas, 63 sectores/pista, 77578 cilindros
Unidades = cilindros de 1008 * 512 = 516096 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1       38250    19277968+   7  HPFS/NTFS
La partición 1 no termina en un límite de cilindro.
/dev/hda2           38251       77578    19821281    f  W95 Ext'd (LBA)
La partición 2 no termina en un límite de cilindro.
/dev/hda5           38251       76500    19277968+  83  Linux
/dev/hda6           76501       77578      543280+  82  Linux swap / Solaris

Disco /dev/hdc: 30.0 GB, 30020272128 bytes
255 cabezas, 63 sectores/pista, 3649 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdc1               2        3649    29302560    f  W95 Ext'd (LBA)
/dev/hdc5               2        3649    29302528+   b  W95 FAT32

```Here, you can see I have a Fat32 file system in /dev/hdc5.
Now, you should edit your /etc/fstab file, which handles what thing to mount at start, and where, and how.
So, you have created the mount point at /media/fat32, and your hard drive is at /dev/hdc5 (in my example). now that you have all these things, edit your fstab:```
sudo gedit /etc/fstab
```Now, you should see something like this:```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```As you can see, each line is a device with the corresponding mount point and options. So, you should add a new line:
First, the device location (/dev/hdc5), then, the mount point (/media/fat32), then, the filesystem (vfat), then, the options for the vfat system (auto,user,exec,umask=000), and then, two zeros. Your new line should look as follows:```
/dev/hdc5       /media/fat32 vfat   auto,user,exec,umask=000        0      0
```Now, do a```
sudo mount -a
```And go to Places > Computer. You should see your hard drives mounted. Reboot your computer to see them mounted automatically at each boot.

If you want to add an NTFS filesystem, just chang vfat to ntfs, and the umask=000 option to umask=0222

---

### Post by Peter Alien on 2005-05-15
Suppose FAT32 partition is at: hda1

For mount that partition at Boot do:

cd /etc                 (go to the folder where the file is)
chmod 777 fstab (changes the permissions of the file)
gedit fstab           (edits the file)


include the following line:

/dev/hda1       /mnt/windows    vfat    rw,umask=000     0   0

save the file.


Create a folder where the partition will be mounted:

e.g. :   mkdir /mnt/windows


To mount the partition do:

mount /dev/hda1


and that's it... :)

---

### Post by jodef on 2005-05-15
Permisions in fstab are controlled by the umask, uid and gid options. For instance umask = 000 means all users will have access. If you want only your user to have access then remove umask=000 and add uid=<username> only the user here specified will have access all other users will get a permission denied error. Of course root will have access as well.

So to give user John access but deny all other users access> /dev/hda1 /mnt/windows vfat rw,umask=000 0 0to > /dev/hda1 /mnt/windows vfat rw,uid=John 0 0 
HTH

---

