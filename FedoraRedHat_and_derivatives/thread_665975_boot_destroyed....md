---
title: "/boot destroyed..."
date: 2008-01-12
forum: Fedora/RedHat and derivatives
---

### Post by deathwishr on 2008-01-12
I realize these are the ubuntu forums, but I really need the help and no one on the fedora forums seems able to help.  And as almost everyone uses grub these days...

I'm running fc6 as when I tried to install Vista over the summer it destroyed my whole system.  XP, Vista & a fresh install of grub/fc6 are all now running.  I gave up when school started but I'm taking (real) programming classes again and need my linux box back.

I used the same disk for this clean fc6 install so the kernel version is identical to the first install of my old linux partition.  The old partition is fine but I can't seem to link my new grub to my old install.  I'm at a total loss.  The fresh install is properly reading my old LVM (via dmraid) but that's as far as I've gotten.

To recap: new grub on a new /boot will start a clean install of fc6 but I can't figure out how to get it to load my OLD linux partition.

my grub.conf file:```
default=2
timeout=5
splashimage=(hd0,1)/grub/splash.xpm.gz
hiddenmenu
password --md5 ******************************************
title Fedora Core fresh
        root (hd0,1)
        kernel /vmlinuz-2.6.18-1.2798.fc6 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
        initrd /initrd-2.6.18-1.2798.fc6.img
title Fedora Core broken
        root (hd0,1)
        kernel /vmlinuz-2.6.18-1.2798.fc6 ro root=/dev/VolGroup01/LogVol00 rhgb quiet
        initrd /initrd-2.6.18-1.2798.fc6.img
title Windows XP
        map (hd0) (hd2)
        map (hd2) (hd0)
        rootnoverify (hd2,1)
        chainloader +1
title Windows Vista
        rootnoverify (hd0,0)
        chainloader +1
```
That boots the 'fresh' install but I get the following error when trying 'broken' boot:```
Decompressing Linux...done.
Booting the kernel.
...
   Reading all Physical volumes. This may take a while...
   Found volume group "VolGroup00" using metadata type lvm2
   Found volume group "VolGroup01" using metadata type lvm2
   2 logical volume(s) in volume group "VolGroup00" now active
mount: could not find filesystem '/dev/root'
...
```
Is there a way to 'activate' VolGroup01 instead of the other one?
I'd appreciate any help and can give you guys more information as needed.  I just usually try to fix this sh*t myself in order to learn but I'm at the end of my rope.  Some extra info:

on boot hd0 is hdb, hd1 is hda & hd2 is sda(/b?)
```
#fdisk -l

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14593   117218241    7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       12044    96739328    7  HPFS/NTFS
/dev/hdb2   *       12045       12056       96390   83  Linux
/dev/hdb3           12057       14593    20378452+  8e  Linux LVM

Disk /dev/sda: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       12156    97635037+   f  W95 Ext'd (LBA)
/dev/sda2           12157       14589    19543072+   c  W95 FAT32 (LBA)
/dev/sda3   *       14590       24377    78622110   8e  Linux LVM
/dev/sda5   ?      154879      269088   917382663+  66  Unknown

Disk /dev/sdb: 100.2 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

#fdisk -l /dev/mapper/via_dfdhfggej

Disk /dev/mapper/via_dfdhfggej: 200.5 GB, 200512503808 bytes
255 heads, 63 sectors/track, 24377 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

                    Device Boot      Start         End      Blocks   Id  System
/dev/mapper/via_dfdhfggej1               2       12156    97635037+   f  W95 Ext'd (LBA)
/dev/mapper/via_dfdhfggej2           12157       14589    19543072+   c  W95 FAT32 (LBA)
/dev/mapper/via_dfdhfggej3   *       14590       24377    78622110   8e  Linux LVM
/dev/mapper/via_dfdhfggej5               2       12156    97635006    7  HPFS/NTFS

# mount -l
/dev/mapper/VolGroup00-LogVol00 on / type ext3 (rw)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/hdb2 on /boot type ext3 (rw) [/boot]
tmpfs on /dev/shm type tmpfs (rw)
/dev/mapper/VolGroup01-LogVol00 on /mnt/orig type ext3 (rw)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
sunrpc on /var/lib/nfs/rpc_pipefs type rpc_pipefs (rw)
```

---

### Post by geraldm on 2008-01-13
The file grub.conf that you are using looks odd to me.  In my system I use a very similar setup file /boot/grub/menu.lst
In that file the lines beginning with  
title
root
kernel
initrd
# the above would be followed by a line with the single word "boot"

The "fresh install" you posted shows that grub is falling through the first specification and continuing into the second specification

I would try inserting the "boot" line and a blank line after the initrd line.  Backup the file before making any changes.  I warn that I am not quite sure about this due to the difference in the file names.  It is just something that I would try to see if it alters the outcome.

>on boot hd0 is hdb, hd1 is hda & hd2 is sda(/b?)
The above line looks possibly like a question (I hope), so you are not quite sure whether the boot order is the same as what it originally was?
The boot order should not change unless you make changes to the number of disks or alter your bios settings that affects the order of the disk discovery or you go into the box and change the cables.
If you are uncertain about the disks being recognized correctly, you might look into the UUID
additions.  They create a unique ID for each disk, and put the unique ID into the /etc/fstab file so that each disk can be properly identified.


Gerald

---

### Post by Sef on 2008-01-13
Download [Super GRUB Boot Disk]("http://supergrub.forjamari.linex.org/").  It is an easy way to reinstall GRUB.

Moved to Other OS Talk > Fedora/Red Hat.

---

### Post by deathwishr on 2008-01-13
Actually, the only question was whether my two scsi drives were showing up as one two grub which, upon further inspection, they were.  So that is the correct order.

Grabbed the new Super GRUB disk and it wasn't any help.  Super GRUB, unfortunately, isn't designed to finesse LVM partitions.  My GRUB install is working perfectly.  It defaults to winXP atm but if I select 'Fedora Core fresh' it boots my fresh install normally.  When I select 'Fedora Core Broken' I get that mount error I mention above.  Any idea how to activate an LVM partition?  Super GRUB has tools to activate a physical partition, but not a logical one inside an LVM.

...I understand why you moved the thread here, but I'd considered this a GRUB question.  Although the error comes ones the kernel is loaded...

---

### Post by deathwishr on 2008-01-13
sorry; 
geraldm: grub.conf is equivalent to menu.lst.  I'm guessing you only have the one os which is why yours starts with "title."  You'll notice mine has those blocks of lines, just with added indents and multiple occurances.  GRUB boots fresh, winXP and Vista without fail.  Broken--which is the partition I'm trying to boot--is the only one that fails.

---

