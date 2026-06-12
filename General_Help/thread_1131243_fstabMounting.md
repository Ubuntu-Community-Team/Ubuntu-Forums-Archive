---
title: "fstab/Mounting"
date: 2009-04-20
forum: General Help
---

### Post by Feelin_froggy8877 on 2009-04-20
I followed some directions on a forum page to auto mount my hdd. fat32 lable (storage) I restarted and It  seems to have dissappeared...I reverted all the steps i took and copied my fstab backup back to /etc/fstab and i still cannot find it after reboot...where it normally is, it is listed as a cdrom and it opens my cdrom dir the same as my actual cdrom would open.

This how you can mount windows partitions in ubuntu. You can only read NTFS but you can read and write on FAT32.

1. Run this command to see what partitions are NTFS/FAT32: sudo fdisk -l
you will get something like: /dev/hda1 ... HPFS/NTFS

2. Create a new directory to mount the partition to: sudo mkdir /mnt/windows

2. Backup fstab (which is the file to configure partitions): sudo cp /etc/fstab /etc/fstab_backup

3. Run this command to edit fstab using gedit (you can use any editor) : gksudo gedit /etc/fstab

4. Copy this line to the end of the file and change hd1 with the correct windows partition from step 1:
For NTFS: /dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0
For FAT32: /dev/hda1 /media/windows vfat iocharset=utf8,umask=000 0 0

done!

The next time you restart ubuntu, it will mount automatically. 



here is my fstab now and befor I made the changes...


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

all I did was was add the line...
/dev/sdc9 /media/windows vfat iocharset=utf8,umask=000 0 0...

and then removed it when it didnt work.

Here is what my fdis -l looks like....


Disk /dev/sda: 10.0 GB, 10005037056 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00730072

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1158     9301603+  83  Linux
/dev/sda2            1159        1216      465885    5  Extended
/dev/sda5            1159        1216      465853+  82  Linux swap / Solaris

Disk /dev/sdb: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x81108110

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2481    19928601    7  HPFS/NTFS

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000784c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         522     4192933+   b  W95 FAT32
/dev/sdc2             523       14946   115860780    f  W95 Ext'd (LBA)
/dev/sdc5             523         789     2144646   83  Linux
/dev/sdc6             790        1056     2144646   83  Linux
/dev/sdc7            1057        1323     2144646   83  Linux
/dev/sdc8            1324        1387      514048+  82  Linux swap / Solaris
/dev/sdc9            1388       14946   108912636    b  W95 FAT32

/dev/sdc9 is the 1 I wanna automount and (was) located in ubuntu menu, places, storage...now I get ubuntu, menu,cdrom0???

This is where all my movies and music are at...I need it back! lol Please help.](*,)](*,)](*,)

---

### Post by Darael on 2009-04-20
I don't quite know what the problem is from looking at your fstab, but we might as well start with the basics.

Is there a folder under /media called windows even with the drive unmounted?  If not, open a terminal and enter "sudo mkdir /media/windows".  This is needed because entries in the fstab require the folder to be present already, while the automount feature does not.

PLEASE don't be offended if you know this, I'm just checking.  You never know, after all...

---

### Post by Feelin_froggy8877 on 2009-04-20
There is not..and as I remember there was (cdrom) and (storage) wich was the hdd I was trying to automount...now (storage) is replaced with (cdrom) I don't remember there being a (windows) dir. But I will create it if needed.

None taken ;-)

---

### Post by Darael on 2009-04-20
Basically, wherever you try to mount it, which from your fstab appears to be /media/windows, there needs to be that folder already in place.

---

### Post by Feelin_froggy8877 on 2009-04-20
Ok...I created the (windows) dir
Man, it was nice to get a quick reply on this.

---

### Post by Darael on 2009-04-20
No problem.

---

### Post by Feelin_froggy8877 on 2009-04-20
Well...I like to consider myself at least (novice) with linux...but I [am] still learning, and I guess If I payed a bit more attention to the directions I would have noticed it said to make dir /(etc)/windows and in the line to add to fstab was /(media)/windows....haha Working just fine now. Thanx for the help.\\:D/

---

### Post by Ticketoride on 2009-04-20
> **Feelin_froggy8877 said:**
> You can only read NTFS but you can read and write on FAT32.
You can write to NTFS too.

---

### Post by Feelin_froggy8877 on 2009-04-20
Oh really? How? The file system is fat32 because it really dont matter since there is no system runnin on it and of course didnt think ntfs was writable from linux. almost everything I download is saved to that hdd....wait a sec? I didnt post that?????

---

