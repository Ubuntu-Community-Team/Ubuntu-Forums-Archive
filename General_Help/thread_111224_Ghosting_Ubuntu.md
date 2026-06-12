---
title: "Ghosting Ubuntu?"
date: 2006-01-01
forum: General Help
---

### Post by xxmaddjxx on 2006-01-01
I have been using ubuntu for a couple of months now and am very very happy with it. A lot of the things i have set up however (dual screen, printer sharing) took very time consuming amounts of searching and tweaking. I was wondering if there was a way to Ghost ubuntu or make my own setup disk that would install fresh with all the settings and progs that i have now.

Thanks

---

### Post by z_diver on 2006-01-01
Look into g4l.  It can copy just about any type of partition to anywhere.  
Below is a link to the project on sourceforge.
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)
Chuck

---

### Post by xxmaddjxx on 2006-01-02
thanks, do u just burn the whole package to cd?

---

### Post by z_diver on 2006-01-02
One thing to note about g4l.  It will copy your drive using dd so if you want to make this quicker and smaller it is recommended to zero out the drive.  A utility to do this is provided and it basically makes a file that fills up the blank space of that particular partition.  It is then up to you to remove it.  If you don't, you won't be able to boot and your copy will be larger instead of smaller than it would have been otherwise.

Aside from that I have found the program to be well documented in it's PDF.  The CD is also handy to keep around since it can turn any machine into an ftp server quickly.

And if you don't feel like backing up the entire hard disk check out the following guide in the Ubuntu wiki.  If you just want to keep the settings, that might be the way to go.

[https://wiki.ubuntu.com/BackupYourSystem?highlight=%28backup%29](https://wiki.ubuntu.com/BackupYourSystem?highlight=%28backup%29)

---

### Post by z_diver on 2006-01-02
Yep.  If you have downloaded the iso image, just right click on it and select Write to Disk.  It's so small that it takes very little time and creates a bootable CD with menus.  It is helpful to grab the PDF and have it around while doing the copies.

---

### Post by maglis on 2006-01-02
I would recommend mondo package.


> powerful disaster recovery suite
Mondo is reliable. It backs up your Debian GNU/Linux server or workstation to
tape, CD-R, CD-RW, NFS or hard disk partition. In the event of catastrophic
data loss, you will be able to restore all of your data [or as much as you
want], from bare metal if necessary. Mondo is in use by numerous blue-chip
enterprises and large organizations, dozens of smaller companies, and tens of
thousands of users.

Mondo is comprehensive. Mondo supports LVM, RAID, ext2, ext3, JFS, XFS,
ReiserFS, VFAT, and can support additional file systems easily. It supports
adjustments in disk geometry, including migration from non-RAID to RAID. Mondo
runs on all major Linux distributions and is getting better all the time. You
may even use it to backup non-Linux partitions, such as NTFS.

Homepage: [http://www.mondorescue.org]("http://www.mondorescue.org")

---

### Post by linuxfroggy on 2006-01-04
About Mondo/Mindi, I'am not sure how to get it. The [http://www.mondorescue.org](http://www.mondorescue.org) does not seems to be reachable. OK, you can get it via Synaptic but there is still an issue with the mindi-partimagehack dependance : mindi-partimagehack:
  Depend : libstdc++6 (>=4.0.2) but 4.0.1-4ubuntu9 shall be installed. The issue is known : [http://www.ubuntuforums.org/showthread.php?t=86681](http://www.ubuntuforums.org/showthread.php?t=86681)

LinuxFroggy

---

### Post by yanik on 2006-01-04
Partimage:

>  Description: Partition Image is a Linux/UNIX utility which saves partitions in many formats (see below) to an image file. The image file can be compressed in the GZIP/BZIP2 formats to save disk space, and split into multiple files to be copied on removable floppies (ZIP for example), ... Partitions can be saved across the network since version 0.6.0.

Partition Image will only copy data from the used portions of the partition. For speed and efficiency, free blocks are not written to the image file. This is unlike the 'dd' command, which also copies empty blocks. Partition Image also works for large, very full partitions. For example, a full 1 GB partition can be compressed with gzip down to 400MB.

This is very useful to save partitions to an image in some cases:

    * First you can restore your linux partition if there is a problem (virus, file system errors, manipulation error) . When you have a problem, you just have to restore the partition, and after 10 minutes, you have the original partition. You can write the image to a CD-R if you don't want the image to use hard-disk space.
    * This utility can be used to install many identical PCs. For example, if you buy 50 PCs, with the same hardware, and you want to install the same linux systems on all 50 PCs, you will save a lot of time. Indeed, you just have to install on the first PC and create an image from it. For the 49 others, you can use the image file and Partition Image's restore function.

tried, tested and true.  I used it a lot back when I was on debian unstable/experimental.


Mondo is also very good. Here's a mirror of their site:
[http://ccp14.sims.nrc.ca/ccp/web-mirrors/mondorescue/](http://ccp14.sims.nrc.ca/ccp/web-mirrors/mondorescue/)


Yanik

---

### Post by squirrelyosis on 2006-01-04
I used Acronis TrueImage to "ghost" my Ubuntu install.  I've done it several times and restored the image to different drives with success.  Norton Ghost will not work for this definetly, but try out Acronis if you can get your hands on a  copy ;)

---

### Post by linuxfroggy on 2006-01-06
Hello,

Just a question for the ones who have been using Mondi / Mindi, did you try to create a disk with mindi a what was the result when selecting your own kernel. On my own instal, I get mindi looking for Lilo though I use Grub. I was wondering if this can lead to an issue when using Mondo to backup ?

```

sudo mindi
Password:
Mindi Linux mini-distro generator v1.04 by Hugo Rabson
Latest Mindi is available from http://www.mondorescue.org
BusyBox sources are available from http://www.busybox.net
------------------------------------------------------------------------------
Do you want to use your own kernel to build the boot disk (y/n) ?y
Would you like to use LILO (instead of syslinux)
for your boot CD/floppies (y/n) ?y
Analyzing dependency requirements                               92%     /Where a re your LVM-Tools? Couldn't find /sbin/lvmiopversion
                                                                Done.
Making complete dependency list                                 Done.
Analyzing your keyboard's configuration.
Adding the following keyboard mapping tables:                   Done.
Assembling dependency files..................................................... .............                                                   Done.
The files have been subdivided into 6 directories.
Your mountlist will look like this:-
    Finding all volume groups
  No volume groups found
  No volume groups found
  No volume groups found
  No volume groups found
        DEVICE          MOUNTPOINT      FORMAT          SIZE (MB)

Incapable d'ouvrir proc
        /dev/hda3       /               ext3              23462
        /dev/hda5       swap            swap               1027
        /dev/hdb2       /mnt/hdb2       ext3              97245
        /dev/hdd1       /mnt/hdd1       ext3              39260
    Finding all volume groups
  No volume groups found
  No volume groups found
  No volume groups found
  No volume groups found
Tarring and zipping the groups.....................             Done.
Creating data disk #1...#2...#3...#4...#5...#6...               Done.
Making 1722KB boot disk.....................You are running a 2.6 kernel, either  completely without ext2
or with ext2 as a module. Good. Using a cpio initrd image.
2956 blocks
......OK, you don't have a /boot/boot.b file, which is odd because most _good_ L inux distributions come with one, even if it's only a softlink
cat: /etc/lilo.conf: Aucun fichier ou répertoire de ce type
Nor can I find it from your /etc/lilo.conf file. This is very odd.
I'm going to use ''
cp: fichier cible manquant
Pour en savoir davantage, faites: « cp --help ».
CBBF -- warning -- cannot find your boot.b file. That's it, I quit... (j/k)
1440+0 enregistrements lus.
1440+0 enregistrements écrits.
1474560 bytes transferred in 0,016624 seconds (88701147 bytes/sec)
mke2fs 1.38 (30-Jun-2005)
OK, you don't have a /boot/boot.b file, which is odd because most _good_ Linux d istributions come with one, even if it's only a softlink
cat: /etc/lilo.conf: Aucun fichier ou répertoire de ce type
Nor can I find it from your /etc/lilo.conf file. This is very odd.
I'm going to use ''
cp: fichier cible manquant
Pour en savoir davantage, faites: « cp --help ».
CBBF -- warning -- cannot find your boot.b file. That's it, I quit... (j/k)
/usr/sbin/mindi: line 1745: lilo: command not found
Warning - failed to create 1.44MB boot/root floppies
Warning! Failed to create 1.72MB boot image. Please reduce your kernel's size
if you want to make a 1.72MB floppy floppy disk.
Making 2880KB boot disk.....................You are running a 2.6 kernel, either  completely without ext2
or with ext2 as a module. Good. Using a cpio initrd image.
5008 blocks
......OK, you don't have a /boot/boot.b file, which is odd because most _good_ L inux distributions come with one, even if it's only a softlink
cat: /etc/lilo.conf: Aucun fichier ou répertoire de ce type
Nor can I find it from your /etc/lilo.conf file. This is very odd.
I'm going to use ''
cp: fichier cible manquant
Pour en savoir davantage, faites: « cp --help ».
CBBF -- warning -- cannot find your boot.b file. That's it, I quit... (j/k)
... 2880KB boot disk was created OK                             Done.
In the directory '/root/images/mindi' you will find the images:-
mindi-bootroot.2880.img    mindi-data-1.img    mindi-data-2.img    mindi-data-3. img    mindi-data-4.img    mindi-data-5.img    mindi-data-6.img
Would you like to create boot+data floppy disks now (y/n) ?n
Shall I make a bootable CD image? (y/n) n
Finished.

Boot and data disk images were created.

```

Best regards,

LinuxFroggy

---

