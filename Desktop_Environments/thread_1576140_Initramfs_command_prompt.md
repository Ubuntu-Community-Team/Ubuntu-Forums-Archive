---
title: "Initramfs command prompt"
date: 2010-09-16
forum: Desktop Environments
---

### Post by Linuxneophyte on 2010-09-16
While a video was playing from Youtube my Ubuntu 10.04 system locked up solid. I did a hard power down, and when it came back up, it went to busy box initramfs command prompt.

I rebooted and tried the recovery and it goes to a (DRDY Error) 

HELP!!!!

---

### Post by Linuxneophyte on 2010-09-16
I found that my /dev/sda5 in GRUB has been replaced with UUID=XXXXXXXXXXXXXXXX a long string of Alphanumeric. If this is any additional help.

---

### Post by tsaowang on 2010-09-17
Hi,

Had the exact same problem yesterday after a fresh install.

Try to boot with a live cd or at initramfs busybox after 1 minute or so hit exit then enter


Next :

Edit grub.cfg this way :


 **#sudo chmod 777 /boot/grub/grub.cfg**

**#sudo vi /boot/grub/grub.cfg**

 - Replace the UUID entries with your /dev/sdx :


 ### BEGIN /etc/grub.d/10_linux ###
menuentry ‘Ubuntu, avec Linux 2.6.32-22-generic’ –class ubuntu –class
gnu-linux –class gnu –class os {
        recordfail
        insmod ext2
        set root=’(hd2,1)’
        search –no-floppy –fs-uuid –set 91e6e215-0557-4ba6-bb06-e60a23d197b1
        linux /boot/vmlinuz-2.6.32-22-generic
root=**UUID=91e6e215-0557-4ba6-bb06-e60a23d197b1** ro   quiet splash
        initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry ‘Ubuntu, avec Linux 2.6.32-22-generic (mode de récupération)’
–class ubuntu –class gnu-linux –class gnu –class os {
        recordfail
        insmod ext2
        set root=’(hd2,1)’
        search –no-floppy –fs-uuid –set 91e6e215-0557-4ba6-bb06-e60a23d197b1
        echo ‘Chargement de Linux 2.6.32-22-generic …’
        linux /boot/vmlinuz-2.6.32-22-generic
root=**UUID=91e6e215-0557-4ba6-bb06-e60a23d197b1** ro single
        echo ‘Chargement du disque mémoire initial…’
        initrd /boot/initrd.img-2.6.32-22-generic
}
menuentry ‘Ubuntu, avec Linux 2.6.31-22-generic’ –class ubuntu –class
gnu-linux –class gnu –class os {
        recordfail
        insmod ext2
        set root=’(hd2,1)’
        search –no-floppy –fs-uuid –set 91e6e215-0557-4ba6-bb06-e60a23d197b1
        linux /boot/vmlinuz-2.6.31-22-generic
root=**UUID=91e6e215-0557-4ba6-bb06-e60a23d197b1** ro   quiet splash
        initrd /boot/initrd.img-2.6.31-22-generic
}
menuentry ‘Ubuntu, avec Linux 2.6.31-22-generic (mode de récupération)’
–class ubuntu –class gnu-linux –class gnu –class os {
        recordfail
        insmod ext2
        set root=’(hd2,1)’
        search –no-floppy –fs-uuid –set 91e6e215-0557-4ba6-bb06-e60a23d197b1
        echo ‘Chargement de Linux 2.6.31-22-generic …’
        linux /boot/vmlinuz-2.6.31-22-generic
root=**UUID=91e6e215-0557-4ba6-bb06-e60a23d197b1** ro single
        echo ‘Chargement du disque mémoire initial…’
        initrd /boot/initrd.img-2.6.31-22-generic
}
### END /etc/grub.d/10_linux ##



 
 - Close VI once you're done (ESC :x)


 **#sudo chmod 444 /boot/grub/grub.cfg**

 Final step edit /etc/default/grub :


 **#sudo vi /etc/default/grub**

 - Uncomment the following line :


 # Uncomment if you don’t want GRUB to pass « root=UUID=xxx » parameter to Linux
**#GRUB_DISABLE_LINUX_UUID=true**
 



- Close VI once you're done (ESC :x)


 **#sudo update-grub**
 **#sudo shutdown -r**


**And everything should be alright now**


[B];)
[/B]

---

### Post by Linuxneophyte on 2010-09-17
I tried this, but my system will not take me to a command prompt. IT is either a [initramfs] or locked up.

I found on the forums I needed to edit the grub as was stated above, but by using a live cd.

I did boot into live cd and did *sudo fdisk - l*

[I]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc466c466

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        7358    59095102+   7  HPFS/NTFS
/dev/sda2            7359       12162    38582273    5  Extended
/dev/sda5            7359       12162    38582272   83  Linux
ubuntu@ubuntu:~$ [/I]

Then I tried the [I]sudo mount /dev/sda5 /mnt
[/I]

This was what I got back

[I]ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ 
[/I]

Any Help would be appreciated. This is my primary work laptop, I have an investors meeting tomorrow and the presentation is on this laptop.

Thanks In Advance!  ):P

---

### Post by scorchgeek on 2010-09-17
The mount command help says to use the switch
```
-t fstype
```.

Perhaps you could try with
```
sudo mount -t ext3 /dev/sda5 /mnt
```

assuming your HD is an ext3 filesystem? The command worked in my test with an NTFS filesystem and the proper paths for my system; I didn't have a spare ext3 one to try with.

---

### Post by scorchgeek on 2010-09-17
You might also see if you get helpful information from the recommended dmesg | tail.

---

### Post by Linuxneophyte on 2010-09-17
This was the result

[I]ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ dmesg | tail
[ 4111.937500] JBD: IO error -5 recovering block 32632 in log
[ 4111.937504] JBD: Failed to read block at offset 32633
[ 4111.937507] JBD: IO error -5 recovering block 32633 in log
[ 4111.937511] JBD: Failed to read block at offset 32634
[ 4111.937514] JBD: IO error -5 recovering block 32634 in log
[ 4111.937518] JBD: Failed to read block at offset 32635
[ 4111.937520] JBD: IO error -5 recovering block 32635 in log
[ 4112.043584] JBD: recovery failed
[ 4112.043591] EXT4-fs (sda5): error loading journal
[ 4600.726734] EXT3-fs: sda5: couldn't mount because of unsupported optional features (240).
[/I]ubuntu@ubuntu:~$

---

### Post by Linuxneophyte on 2010-09-17
I did it again after realizing /dev/sda5 is Ext4 not Ext3

[I]ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
[/I]

---

### Post by Linuxneophyte on 2010-09-21
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc466c466

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        7358    59095102+   7  HPFS/NTFS
/dev/sda2            7359       12162    38582273    5  Extended
/dev/sda5            7359       12162    38582272   83  Linux
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda5 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ dmesg | tail
[  231.368126] Buffer I/O error on device sr0, logical block 358116
[  232.502462] sr 0:0:1:0: [sr0] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  232.502469] sr 0:0:1:0: [sr0] Sense Key : Illegal Request [current] 
[  232.502477] Info fld=0x576e4, ILI
[  232.502479] sr 0:0:1:0: [sr0] Add. Sense: Illegal mode for this track
[  232.502487] sr 0:0:1:0: [sr0] CDB: Read(10): 28 00 00 05 76 e4 00 00 01 00
[  232.502501] end_request: I/O error, dev sr0, sector 1432464
[  232.502508] Buffer I/O error on device sr0, logical block 358116
[  268.436222] hci_cmd_task: hci0 command tx timeout
[  539.488426] EXT4-fs (sda5): VFS: Can't find ext4 filesystem

---

### Post by LinuxPhreak on 2010-09-21
I got the initramfs error when using Ubuntu Server 10.04 on a P2 computer running 64MB RAM and 40GB HDD. It happened to me after I did a Kernel Upgrade. When I reinstalled it on newer hardware the problem never happened again. I was under the belief it was do to old hardware.

---

### Post by Linuxneophyte on 2010-09-21
Nothing like that here. Been running 10.04 since April. did a clean install on my linux part. and has worked great. The other day my son was showing me a Youtube video and the system locked up. let it try to correct itself, by leaving it alone for about 15 minutes, but no luck. Powered it down and it came back up with the initramfs. Now it is sitting with a sh:grub after trying a few of the suggestions.

This is my primary work computer, and I am in the middle of negotiation with major investors for my business.

](*,)](*,)](*,)](*,)


HELP!!!

---

### Post by Linuxneophyte on 2010-09-22
> It is un American to not like Open Source. It is un Christian to not follow the ways of Open Source. 

Amen to that!! Long Live Open Source!!

---

### Post by Linuxneophyte on 2010-09-22
**This is my fisk -l for my system booting with LiveCD**

[I]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc466c466

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2        7358    59095102+   7  HPFS/NTFS
/dev/sda2            7359       12162    38582273    5  Extended
/dev/sda5            7359       12162    38582272   83  Linux
ubuntu@ubuntu:~$ 

[/I]


**This is what I get when I try to Mount my sda5 above**
[I]
ubuntu@ubuntu:~$ sudo mount -t /dev/sda5 /mnt
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
ubuntu@ubuntu:~$ [/I]

Any ideas?!?!?

---

### Post by Linuxneophyte on 2010-09-24
Bump!

---

### Post by Linuxneophyte on 2010-09-27
Bump!

---

### Post by Linuxneophyte on 2010-09-30
Bump!

---

### Post by psusi on 2010-09-30
Your hard disk appears to be shot.  Boot the livecd and fire up the disk utility and look at the SMART diagnostics.  Run the extended self test.

---

### Post by Linuxneophyte on 2010-10-02
SMART Drive says the disc is good. I can boot the system up with Helix and pull up all my windows info. My Unbuntu  is not showing up. It shows I have and Ext3 partition, but it does not show to have a bootable Linux OS.

Any Ideas?!?

---

