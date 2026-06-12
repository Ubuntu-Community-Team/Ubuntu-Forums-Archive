---
title: "Change Factory Restore to Gutsy not Fiesty"
date: 2007-12-14
forum: Dell  Ubuntu Support
---

### Post by #!/bin/bash on 2007-12-14
The purpose of this HowTo is to change the Dell Factory Restore which comes with the Dell's preloaded with Ubuntu-7.04. So that if you have to do a factory restore you will end up with Ubuntu-7.10 and not Ubuntu-7.04.

WARNING: Please use the following information with extreme caution. Also know that I have not tested this procedure. **EDIT: Yes I have tested it and it didn't work as first posted but after making a few changes it now works.** I have every confidence that this should work but I'm not willing to wipe out my installation to verify that it does. If I ever have a catastrophic failure that is when I will test this. Maybe someone from Dell would be kind enough to look this over and to see if I'm on the right track.

The system I have is the Dell Dimension E520. The factory configuration of the hard drive is as follows:
/dev/sda1   Dell Utility
/dev/sda2   W95 FAT32 
/dev/sda3   Linux
/dev/sda4   W95 Ext'd (LBA)
/dev/sda5   Linux swap / Solaris
/dev/sda6   Linux

I have repartitioned my system and added these partitions:
/dev/sda7 on /home type ext3 (rw)
/dev/sda8 on /home/ftp/pub type ext3 (rw)
/dev/sda9 on /games type ext3 (rw)
/dev/sda10 on /data type ext3 (rw)

The partitions we will be concerned with are:
sda2 = Dell Factory Restore Partition
sda3 = Boot Partition
sda6 = / (filesystem root)

I mounted /dev/sda2 at /mnt/sda2

The tarball that contains the Ubuntu-7.04 filesystem is:
/mnt/sda2/ub704img.tgz

The script that installs Ubuntu-7.04 (ub704img.tgz) is in:
/mnt/sda2/scripts/bootstrap/14-untar-os.sh

```
$ cat 14-untar-os.sh
#!/bin/sh

maybe_break2 $(basename $0)

mount $INSTALL_PART /mnt/install
cd /mnt/os
gzip -d -c /mnt/install/ub704img.tgz | tar xpf - 
cd /
umount /mnt/install
```

So what do we need to do to recreate this tarball for gutsy?
[list=1]
[*] Download ubuntu-7.10-desktop-i386.iso
[*] Burn a cd and mount it at /media/cdrom, or just mount the iso using /dev/loop.
[*] Mount the squashfs image located at /media/cdrom/casper/filesystem.squashfs 
You must be root to do this:
# mount /media/cdrom/casper/filesystem.squashfs /mnt/staging -t squashfs -o loop
[*] Now you have to create a boot tarball because the one on the iso file has no grub menu. You have a couple options here: [list=a]
[*] You could copy the boot directory to another directory so you can make changes.
[*] If you are using the vmlinuz-2.6.22-14-generic kernel you can create the boot tarball from your existing /boot directory. [/list]
[*] To create the boot tarball run these commands as root:
 # Edit /boot/grub/menu.lst and make sure there is an entry for vmlinuz-2.6.22-14-generic
 # cd /;tar czpf /tmp/ub710boot.tgz /boot
 # mv /tmp/ub710boot.tgz /mnt/sda2/
[*] To create the filesystem tarball run these commands as root:
 # cd /mnt/staging
 # tar -czpf /tmp/ub710img.tgz .         <- don't forget the dot!
 # rm /mnt/sda2/ub704img.tgz           #Make a backup first
 # mv /tmp/ub710img.tgz /mnt/sda2/
[*] # edit /mnt/sda2/scripts/bootstrap/14-untar-os.sh
Change ub704img.tgz to ub710img.tgz
Add another line after that line, the result should look like this:
#!/bin/sh

maybe_break2 $(basename $0)

mount $INSTALL_PART /mnt/install
cd /mnt/os
gzip -d -c /mnt/install/ub710img.tgz | tar xpf -
gzip -d -c /mnt/install/ub710boot.tgz | tar xpf -
cd /
umount /mnt/install

[*] If you have drivers you need you can have the restore function install your own deb's by putting them in /mnt/sda2/debs/main/.
[/list] That should do it. Now if you are forced to do a factory restore you should at least end up with a gutsy system and not have to go back to feisty. I suspect you could use this same procedure with Kubuntu or your favorite flavor of ubuntu.

WARNING: The factory restore will repartition /dev/sda and wipe out any extended partitions you might have created. To prevent this from happening I suggest you look at the file /mnt/sda2/scripts/bootstrap/10-format.sh and comment out lines 6,7 & 14
```
#!/bin/sh

maybe_break2 $(basename $0)

# Step 1: delete possible 3rd/4th partition
#echo "0,0,0,-" | sfdisk -uS -N3 --force $BOOTDEV
#echo "0,0,0,-" | sfdisk -uS -N4 --force $BOOTDEV

MemKB=$(cat /proc/meminfo | grep ^MemTotal | cut -d: -f2 | sed 's/^\s*//g' | cut -d' ' -f1)
MemMB=$(( $MemKB / 1024 ))

BOOT_SIZE=200
SWAP_SIZE=$(( $MemMB * 130 / 100 + 10 ))
#echo -ne "n\np\n3\n\n+${BOOT_SIZE}M\nn\ne\n\n\nn\n\n+${SWAP_SIZE}M\nn\n\n\nt\n5\n82\nt\n4\nf\nw\n" | fdisk $BOOTDEV

# Step 3: create filesystem
ln -s /proc/mounts /etc/mtab
mke2fs -j -L os_part $OS_PART
mke2fs -j -L os_part $BOOT_PART

```

Of course if you find errors or corrections...

---

### Post by #!/bin/bash on 2007-12-16
Here is a grub/menu.lst that should work:
```
default         0
timeout         3
hiddenmenu

title           Ubuntu 7.10, Default
root            (hd0,2)
kernel          /vmlinuz root=/dev/sda6 ro quiet splash
initrd          /initrd.img
quiet

title           Ubuntu 7.10, (recovery mode)
root            (hd0,2)
kernel          /vmlinuz root=/dev/sda6 ro single
initrd          /initrd.img

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /memtest86+.bin
quiet

title Reinstall Operating System (WARNING: all Hard Drive data will be LOST!)
        root (hd0,1)
        kernel /vmlinuz debug boot=dellfactory quiet
        initrd /initrd.gz
```
vmlinuz is a symlink pointing to -> vmlinuz-2.6.22-14-generic
initrd.img is symlink pointing to -> initrd.img-2.6.22-14-generic

---

### Post by #!/bin/bash on 2007-12-19
FYI, I also tried this with Kubuntu and that also works. It's the exact same procedure also.

Would someone mind checking the script:
/factory_restore_partition/scripts/bootstrap/10-format.sh 
And see if in fact they are giving both partitions the same label or did I screw up that script somehow.
mke2fs -j -L os_part $OS_PART
mke2fs -j -L os_part $BOOT_PART

---

### Post by natehall on 2007-12-20
Sure is tempting to try this, but I've got too much stuff at risk. I have a old HP pavillion set up with Gutsy that I can manage all day though. I shall try it on that.

---

### Post by #!/bin/bash on 2007-12-20
> **natehall said:**
> Sure is tempting to try this, but I've got too much stuff at risk. I have a old HP pavillion set up with Gutsy that I can manage all day though. I shall try it on that.
There is a script which you can specify the OS partition to install the filesystem on. That way you could test it on a different partition to see if it works first. Then you set it up so if you have a disaster it will install on your normal partition. 
The script is loacted at:
/factory_restore_partition/scripts/bootstrap/01-environment.sh
On my system factory_restore_partition is /dev/sda2.

 This is not a perfect solution and when you do this you will need to tweek some settings, hostname, fstab, users, passwords ... This is only intended to save you the additional step of upgrading to Gutsy after a factory restore. Also remember as long as you downloaded the iso you might as well burn the CD. That way if the factory restore doesn't work you can still get Gutsy installed using the CD.

---

### Post by natehall on 2007-12-20
I've burned the DVD but I don't know what to do with it!

---

### Post by natehall on 2007-12-21
Got it working , just have to be really quick in the boot menu to hit f12!

---

