---
title: "grub not installed properly"
date: 2009-02-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dougleduck on 2009-02-09
I've tried to install intrepid dual booting with vista. As I wanted to try few more distros I wanted to have a seperate /boot/grub/ partition. (Also have seperate /home and / partitions). 

Install seems to have gone fine, but got errors after trying to install grub. Means that although ubuntu seems to be on / grub isnt the boot manager and just goes straight into vista.

Tried to install it using the terminal but no luck. Can anyone walk me through installing it? 

Tried to put /boot/grub/ on sda5 (size is about 300 MB), but don't quite know what I'm doing yet.

This is all fresh install, no files to be lost.

---

### Post by caljohnsmith on 2009-02-09
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to the Live CD desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by dougleduck on 2009-02-09
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  Grub
    Boot sector info:  Grub0.97 is installed in the boot sector of sda5 and 
                       looks at sector 93714697 of the same hard drive for 
                       the stage2 file. A stage2 file is at this location on 
                       /dev/sda. Stage2 looks on partition #5 for 
                       /grub/menu.lst.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /etc/fstab

sda8: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda9: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda10: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda11: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda12: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda13: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63       257,039       256,977  de Dell Utility
/dev/sda2             258,048    21,229,567    20,971,520   7 HPFS/NTFS
/dev/sda3    *     21,237,930    93,691,079    72,453,150   7 HPFS/NTFS
/dev/sda4          93,691,080   625,137,344   531,446,265   5 Extended
/dev/sda5          93,691,143    94,301,549       610,407  83 Linux
/dev/sda6          94,301,613   136,247,264    41,945,652  83 Linux
/dev/sda7         136,247,328   167,702,534    31,455,207  83 Linux
/dev/sda8         167,702,598   178,192,979    10,490,382  83 Linux
/dev/sda9         178,193,043   188,683,424    10,490,382  83 Linux
/dev/sda10        188,683,488   199,173,869    10,490,382  83 Linux
/dev/sda11        199,173,933   209,664,314    10,490,382  83 Linux
/dev/sda12        620,944,443   625,137,344     4,192,902  82 Linux swap / Solaris
/dev/sda13        209,664,378   620,944,379   411,280,002  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D9-0204" TYPE="vfat" 
/dev/sda2: UUID="BAEC98ADEC986603" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda3: UUID="E0D69B96D69B6B92" LABEL="OS" TYPE="ntfs" 
/dev/sda5: UUID="45ad75ab-c298-4017-8d75-850e50403f00" TYPE="ext3" 
/dev/sda6: UUID="7e9ffe2a-4866-4405-975f-ea63ecadec09" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="40b4d402-523e-4738-86b8-992cfd8fd20b" TYPE="ext3" 
/dev/sda8: UUID="6f9e07ec-252b-412d-ae09-725aac8f227e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda9: UUID="281cf2e2-3b9c-4c0f-9145-20d7a5616cf5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda10: UUID="b390f299-3791-4dcc-b01c-a4e96c21ffc6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: UUID="2514c9f8-53ee-41b3-a239-dcc4acf9646e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda12: UUID="aadda235-9cc5-461c-a33d-9ae821176a21" TYPE="swap" 
/dev/sda13: UUID="362faf1d-9237-4ae5-b3b2-21a83e12a4fc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/loop0: TYPE="squashfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda7 on /media/disk type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda5 on /mnt/root type ext3 (rw)
none on /mnt/root/proc type proc (rw)
/dev on /mnt/root/dev type none (rw,bind)

=================== sda5: Location of files loaded by Grub: ===================


  47.9GB: grub/stage2

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=40b4d402-523e-4738-86b8-992cfd8fd20b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=45ad75ab-c298-4017-8d75-850e50403f00 /boot/grub      ext3    relatime        0       2
# /dev/sda6
UUID=7e9ffe2a-4866-4405-975f-ea63ecadec09 /home           ext3    relatime        0       2
# /dev/sda12
UUID=aadda235-9cc5-461c-a33d-9ae821176a21 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  83.1GB: boot/initrd.img-2.6.27-7-generic
  83.1GB: boot/vmlinuz-2.6.27-7-generic
  83.1GB: initrd.img
  83.1GB: vmlinuz

```

---

### Post by caljohnsmith on 2009-02-09
So when you installed Ubuntu, did you click the "Advanced" button near the end of the installation and specify to not have Grub installed? It looks like that is what you did, and that means you'll need a menu.lst for your dedicated Grub partition. Also, you'll need to install Grub to the MBR in order to have a multi-boot setup with sda5 as your dedicated Grub partition. How about doing the following from your Live CD:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda --recheck
```
Then save the the attached "menu.lst.txt" to your desktop, and do:
```
sudo mv ~/Desktop/menu.lst.txt /mnt/boot/grub/menu.lst

```
After that, reboot, and let me know how far you get. We can work from there if necessary.

---

### Post by dougleduck on 2009-02-09
Brilliant! Thanks a lot.

I did that the first time, but re-installed and went with the default second time. Maybe when I tried to install it, managed that much.

Now onto some more distros :D.

---

### Post by caljohnsmith on 2009-02-09
Glad that worked OK; cheers and have fun trying different distros. :)

---

