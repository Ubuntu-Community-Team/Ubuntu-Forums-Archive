---
title: "Migrating to an Encrypted File System with Ubuntu GNU/Linux"
date: 2011-03-19
forum: Desktop Environments
---

### Post by Zebis on 2011-03-19
Hello, there may be others of these available, but I was not able to find one so I threw together a guide that describes migrating an existing Ubuntu installation to an encrypted installation with preboot authentication.  I hope this is helpful to someone; when I needed to do this it took me quite a while to compile the steps.

This is copied from a guide I put together for another purpose so some of the dialog may be a bit off for this forum.

I'm posting here because a fair amount of info came from this forum and Ubuntu was the base for my test system.

**LUKS vs. PGP WDE**
Back in the Ubuntu 9 days PGP WDE offered an easy to implement and support FIPS compliant whole disk encryption system. PGP, however, has not been updated to support anything beyond Ubuntu 9.04; maybe they are having hard times or have not marketed PGP WDE well enough to fund continued development.

Since we can't be using old and obsolete software, we need something robust, secure, and fully modern. LUKS is the answer. Many people may thinking about the FIPS compliance situation. The way to think about this is simple; FIPS is one small part of the equation. The goal is have a fully secure and modern configuration. If we have to use legacy software, the argument can be easily made that the security issues or technical limitations associated with a significantly previous version or legacy operating system outweigh the one characteristic of FIPS compliance. A current GNU/Linux installation paired with LUKS offers a robust, secure, and modern configuration without the risk associated with legacy systems.

**Objective**
This document describes the process of converting a "clear" Ubuntu GNU/Linux installation to an encrypted installation. This guide was written using Ubuntu 10.04 LTS x64. The encryption system used by this guide is LUKS/dm-crypt.

**Information**
This guide assumes the installation to be migrated is installed on a single partition.

This guide is a first version guide written quickly and does not include some specific steps such as commands to format a partition thus it requires at least low tier1 support or technical knowledge.

Items enclosed in "<>" are variables dependent on your specific configuration.

Most of the commands in this guide need to be executed with root privileges.

**Equipment Needed**
Computer
Ubuntu Boot Media
External storage (hard drive, server, etc.)

**Process**
[B]Make any necessary backups and/or images. Clonezilla works well for this
Boot with Ubuntu Boot Media[/B]
**Install LVM2**
sudo apt-get update && sudo apt-get -y install lvm2
Tar the current installation to an external drive
1.Mount external storage and volume to migrated
2.cd to the mount point of the source volume
3.sudo tar cpSf <archive> ./*

**Unmount external storage and source volume**
**Overwrite drive if desired**
Using your method of choice, overwrite the drive if you would like there to be no chance (for practical purposes) of forensic retrieval of your personal information.

**Create Partition Table**
This section assumes the drive containing the data to be migrated is sda.
1.Fdisk /dev/sda
2.If you skipped the above overwrite step, delete root and swap partitions
3.Create a new partition of 200MB (this will be the boot partition)
4.Create an extended partition consuming the remaining space
5.Create a logical partition consuming the remaining space

**Format the primary partition as ext4**
**Establish Encryption**
This assumes that your logical partition is partition 5
1.cryptsetup -y -s 256 -c aes-cbc-essiv:sha256 luksFormat /dev/sda5
2.Enter your desired passphrase when prompted

**Open new encrypted volume**
1.cryptsetup luskOpen /dev/sda5 <desired reference>

**Create LVM (root and swap)**
1.pvcreate /dev/mapper/<desired reference>
2.vgcreate <desired volume group name> /dev/mapper/<desired reference>
3.lvcreate -LxG -nswap <desired volume group name>   (x = desired size of swap partition)
4.lvcreate -l 100%FREE -nrootfs <desired volume group name>

**Format root and swap**
1.mkswap /dev/<desired volume group name>/swap
2.mkfs.ext4 /dev/<desired volume group name>/rootfs

**Restore Tar archive**
1.Mount your new root file system /dev/<desired group name>/rootfs
2.mount external storage
3.cd to your new root file system
4.extract tar archive using tar xSpf <tar archive>

**Prepare boot partition**
1.Mount boot partition created and formatted earlier
2.move the contents of rootfs/boot to root of the new boot partition

**Update configuration to support encryption and new /boot location**
1.List contents of /dev/mapper. Here you will see references to your new root and swap space. This will be used in the following steps.
2.Find UUID of boot partition by using "blkid" command
3.Update /etc/fstab as follows

---1.for root file system:  /dev/mapper/<root space>   /   ext4   errors=remount-ro   0  1

---2.for boot partition:  UUID=<UUID of boot partition>   /boot    ext4    defaults    0   2

---3.For swap space: /dev/mapper/<swap space>    none    swap   sw   0   0
4.Update /etc/crypttab as follows

---1.Find UUID of LVM (/dev/sda5 in this example) by using the "blkid" command

---2.add the following two lines

------1.sda5_crypt <UUID of logical partition containing LVM>    none   luks

------2.cryptswap /dev/mapper/<swap space>   /dev/urandom   swap,cipher=aes-cbc-essiv:sha256
5.Create the file /etc/initramfs-tools/conf.d/cryptroot with the following lines

---1.target=sda5_crypt,source=UUID=<UUID of sda5>,key=none,rootdev,lvm=<root file system as shown under /dev/mapper/ (this is only the volume name, not the path)>

---2.target=sda5,crypt,source=UUID=<UUID of sda5>,key=none,lvm=<swap space as shown under /dev/mapper (this is only the volume name, not the path)>

**Prepare to chroot to new rootfs**
1.For simplicity unmount /boot and /rootfs. The mount point in the following steps is provided as an example, there is no technical reason to use this mount point. The following commands assume the boot partition is sda1
2.mount /dev/<desired volume group name>/rootfs /mnt
3.mount /dev/sda1 /mnt/boot
4.mount --bind /proc /mnt/proc
5.mount --bind /dev /mnt/dev
6.cp /etc/resolv.conf /mnt/etc/resolv.conf

**chroot to new rootfs and install packages, update initramfs, update grub**
1.chroot /mnt
2.apt-get update && apt-get -y install cryptsetup ecryptfs-utils lvm2
3.grub-install /dev/sda
4.update-grub
5.update-initramfs -k all -c   (this may present an error about crypttab, but that can be disregarded)
6.exit

**Unmount volumes and reboot**
1.cd to root directory
2.umount /mnt/proc /mnt/dev /mnt/boot /mnt
3.shutdown -r now

**Conclusion**
Upon reboot you will be prompted for your LUKS password when the encrypted partition is accessed.

**Sources**
The below sources were helpful in compiling this procedure

Ubuntu 10.04 Alt install as reference
[http://www.debian-administration.org/articles/577](http://www.debian-administration.org/articles/577)
[https://wiki.archlinux.org/index.php/GRUB2#Combining_the_use_of_UUID.27s_and_basic_scripting](https://wiki.archlinux.org/index.php/GRUB2#Combining_the_use_of_UUID.27s_and_basic_scripting)
[https://bbs.archlinux.org/viewtopic.php?id=112803](https://bbs.archlinux.org/viewtopic.php?id=112803)
[http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/](http://www.webtechquery.com/index.php/2010/04/install-grub2-from-live-cd/)
[http://ubuntuforums.org/showthread.php?t=1641722](http://ubuntuforums.org/showthread.php?t=1641722)
[http://ubuntuforums.org/showthread.php?t=1641722](http://ubuntuforums.org/showthread.php?t=1641722)
[http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html](http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html)
[http://ubuntuforums.org/showthread.php?t=1471961](http://ubuntuforums.org/showthread.php?t=1471961)
[http://www.brandonhutchinson.com/Mounting_a_Linux_LVM_volume.html](http://www.brandonhutchinson.com/Mounting_a_Linux_LVM_volume.html)
[http://www.g-loaded.eu/2005/11/10/encrypt-devices-using-dm-crypt-and-luks/](http://www.g-loaded.eu/2005/11/10/encrypt-devices-using-dm-crypt-and-luks/)
[http://ubuntuforums.org/showthread.php?t=238867](http://ubuntuforums.org/showthread.php?t=238867)
[http://ubuntuforums.org/showthread.php?t=404346](http://ubuntuforums.org/showthread.php?t=404346)
[http://element14.wordpress.com/2007/08/13/encrypt-a-disk-using-luks-on-linux/](http://element14.wordpress.com/2007/08/13/encrypt-a-disk-using-luks-on-linux/)
[http://forums.fedoraforum.org/showthread.php?t=210083](http://forums.fedoraforum.org/showthread.php?t=210083)
[http://ubuntuforums.org/showthread.php?t=1521023](http://ubuntuforums.org/showthread.php?t=1521023)
[http://ubuntuforums.org/showthread.php?t=1597246](http://ubuntuforums.org/showthread.php?t=1597246)
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-install)
[http://pzolee.blogs.balabit.com/2010/07/grub-helyreallitas-titkositott-es-lvm-particiok-eseten/](http://pzolee.blogs.balabit.com/2010/07/grub-helyreallitas-titkositott-es-lvm-particiok-eseten/)
[http://ubuntuforums.org/showthread.php?t=1606644](http://ubuntuforums.org/showthread.php?t=1606644)
[http://www.debian-administration.org/articles/428](http://www.debian-administration.org/articles/428)
[http://blog.gauner.org/blog/tag/luks/](http://blog.gauner.org/blog/tag/luks/)
[http://forums.debian.net/viewtopic.php?f=17&t=57351](http://forums.debian.net/viewtopic.php?f=17&t=57351)
[http://ubuntuforums.org/showthread.php?t=1309205](http://ubuntuforums.org/showthread.php?t=1309205)
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/667060](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/667060)
[https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
[http://forums.linuxmint.com/viewtopic.php?f=46&t=38599](http://forums.linuxmint.com/viewtopic.php?f=46&t=38599)
[http://ubuntuforums.org/showthread.php?p=10162890](http://ubuntuforums.org/showthread.php?p=10162890)
[http://ubuntuforums.org/showthread.php?t=1530532&page=2](http://ubuntuforums.org/showthread.php?t=1530532&page=2)

---

