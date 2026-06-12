---
title: "Dapper Install on RAID using debootstrap"
date: 2006-07-18
forum: Desktop Environments
---

### Post by aeaster on 2006-07-18
I have been running UBuntu on my laptop for over 6 months now and I love it, so much in fact that last week I decided to take the plunge and remove windows completely from my primary desktop and replace it with Dapper.

However, my desktop has an NVidia SATA softraid. This is my first attempt at configuring a fakeraid and after 6 days of studying HowTo's, various configuration documents and forum threads I am somewhat bewildered as I cannot get past debootstrap.

Because of the FakeRAID I am unable to use the Dapper installer, therefore I have turned to debootstrap - These are the steps I have taken so far:

Initially I booted with the Dapper live CD and partitioned my drives as follows:

   # sudo fdisk /dev/sda
   # sudo fdisk /dev/sdb

/boot	+100M	p	sda/b1	-	fd,boot
/	+5G	p	sda/b2	-	fd
Extended	e	sda/b3
swap	+2G	l	sda/b5	-	82
/tmp	+2G	l	sda/b6	-	fd
/usr	+12G	l	sda/b7	-	fd
/home	+5G	l	sda/b8	-	fd
/var	+8G	l	sda/b9	-	fd
/tools	+Rest	l	sda/b10	-	fd


Once I'd re-booted I setup the swap space

   # sudo mkswap /dev/sda5
   # sudo swapon /dev/sda5

Then I loaded the raid1 module

   # sudo modprobe raid1

Next I created a degraded softraid with mdadm

   # sudo mdadm -Cv /dev/md0 -l 1 -n 2 /dev/sda1 missing
   # sudo mdadm -Cv /dev/md1 -l 1 -n 2 /dev/sda2 missing
   # sudo mdadm -Cv /dev/md2 -l 1 -n 2 /dev/sda6 missing
   # sudo mdadm -Cv /dev/md3 -l 1 -n 2 /dev/sda7 missing
   # sudo mdadm -Cv /dev/md4 -l 1 -n 2 /dev/sda8 missing
   # sudo mdadm -Cv /dev/md5 -l 1 -n 2 /dev/sda9 missing
   # sudo mdadm -Cv /dev/md6 -l 1 -n 2 /dev/sda10 missing


'cat /proc/mdstat' showed that each array had created correctly -

Personalities : [raid1]
md6 : active raid1 sda10[0]
      86694656 blocks [2/1] [U_]
md5 : active raid1 sda9[0]
      7823552 blocks [2/1] [U_]
md4 : active raid1 sda8[0]
      4891648 blocks [2/1] [U_]
md3 : active raid1 sda7[0]
      11727296 blocks [2/1] [U_]
md2 : active raid1 sda6[0]
      1959808 blocks [2/1] [U_]
md1 : active raid1 sda2[0]
      4891712 blocks [2/1] [U_]
md0 : active raid1 sda1[0]
      104320 blocks [2/1] [U_]
unused devices: <none>


Next I formatted the file systems

   # sudo mke2fs -j /dev/md0	
   # sudo mkfs.reiserfs /dev/md1
   # sudo mkfs.reiserfs /dev/md2
   # sudo mkfs.reiserfs /dev/md3
   # sudo mkfs.reiserfs /dev/md4
   # sudo mkfs.reiserfs /dev/md5
   # sudo mkfs.reiserfs /dev/md6


Then I created a temporary file structure to hold my new installation and mounted my partitions.

   # sudo mkdir /target
   # sudo mount -t reiserfs /dev/md1 /target
   # cd /target
   # sudo mkdir boot tmp usr home var tools dev proc sys
   # sudo mount -t ext3 /dev/md0 /target/boot
   # sudo mount -t reiserfs /dev/md2 /target/tmp
   # sudo mount -t reiserfs /dev/md3 /target/usr
   # sudo mount -t reiserfs /dev/md4 /target/home
   # sudo mount -t reiserfs /dev/md5 /target/var
   # sudo mount -t reiserfs /dev/md6 /target/tools
   # sudo mount --bind /dev /target/dev
   # sudo mount -t proc proc /target/proc
   # sudo mount -t sysfs sysfs /target/sys


Now I am ready to install dapper so I mount the CD ROM, install debootstrap and run it

   sudo mkdir /mnt/cdrom
   sudo mount /dev/cdrom /mnt/cdrom
   sudo apt-get install debootstrap
   sudo debootstrap --arch i386 dapper /target file:/mnt/cdrom/ubuntu


The problem is, when I run the above command it errors out with:

ubuntu@ubuntu:/target$ sudo debootstrap --arch i386 dapper /target file:/mnt/cdrom/ubuntu
I: Retrieving Release
I: Retrieving Packages
I: Validating Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
I: Checking component main on file:/mnt/cdrom/ubuntu...
I: Retrieving libatm1
I: Validating libatm1
W: Failure trying to run: chroot /target mount -t proc proc /proc

Only a thought but I have seen one thread that mentioned mounting proc with exec, firstly I am unsure what this means and secondly this was for a legacy version of Debian. I understand if I mount the devices through fstab with 'mount -a' I can add 'defaults' as an option which includes exec??

Any help, much appreciated

---

### Post by aeaster on 2006-07-22
After faffing with debootstrap for much longer than I should have, I decided to take a different approach. So I opened up my box (Shuttle XPC SN25P) and removed the cables from sdb. (I later found I should have removed the cables from sda, but nevermind).

In case any one else is having a similar issues, here are the steps I took to bring up RAID1 on my Shuttle.

Once I'd re-booted I found Ubiquity was happy to install UBuntu for me, well almost. 

The initial step was to fdisk the drive as follows

   # sudo fdisk /dev/sda

/boot	+100M	p	sda1
/	+5G	p	sda2
Extended	e	sda3
swap	+2G	l	sda5
/tmp	+2G	l	sda6
/usr	+12G	l	sda7
/home	+3G	l	sda8
/var	+8G	l	sda9
/tools	+Rest	l	sda10

> t > 1 > fd
> t > 2 > fd
> t > 5 > 82
> t > 6 > fd
> t > 7 > fd
> t > 8 > fd
> t > 9 > fd
> t > 10 > fd
> a > 1
> w

The 'fd' sets the drive to 'raid-autodetect' - This is important

Next i formatted the file systems:

   # sudo mke2fs -j /dev/sda1
   # sudo mkreiserfs /dev/sda2
   # sudo mkswap /dev/sda5
   # sudo mkreiserfs /dev/sda6
   # sudo mkreiserfs /dev/sda7
   # sudo mkreiserfs /dev/sda8
   # sudo mkreiserfs /dev/sda9
   # sudo mkreiserfs /dev/sda10

Then I rebooted to ensure the partitions were seen correctly

Once up and running again with the live CD I ran Ubiquity (the UBuntu installer). I figured as there was no raid to worry about I could run the install on /dev/sda. After choosing manual when partitioning, all of the partitions were seen correctly and I was able to install UBuntu. Once this was done it asked me to re-boot and bingo - UBuntu on /dev/sda.


OK, the next step was to setup a degraded raid using mdadm and then to change some files to allow me to boot from the raid. 

Once I had rebooted again, I booted up with the live CD and ran the following commands to create the degraded arrays

   # sudo mdadm -Cv /dev/md0 -l 1 -n 2 /dev/sda1 missing
   # sudo mdadm -Cv /dev/md1 -l 1 -n 2 /dev/sda2 missing
   # sudo mdadm -Cv /dev/md2 -l 1 -n 2 /dev/sda6 missing
   # sudo mdadm -Cv /dev/md3 -l 1 -n 2 /dev/sda7 missing
   # sudo mdadm -Cv /dev/md4 -l 1 -n 2 /dev/sda8 missing
   # sudo mdadm -Cv /dev/md5 -l 1 -n 2 /dev/sda9 missing
   # sudo mdadm -Cv /dev/md6 -l 1 -n 2 /dev/sda10 missing

By running # cat /proc/mdstat I could see the arrays had been created correctly (You need to look for '(U_)' which shows there is one disc connected to the array). The follow command will show you detailed info about each array.

   # sudo mdadm --misc --detail /dev/md0

There's no reason to use RAID for the swap partition. The kernel itself can stripe swapping on several devices, you just give them the same priority in the fstab file. This setup lets the machine swap in parallel.

Next I mounted the partitions to a temporary location '/target'

   # sudo mkdir /target
   # sudo mount -t reiserfs /dev/md1 /target
   # cd /target
   # sudo mkdir boot tmp usr home var tools dev proc sys
   # sudo mount -t ext3 /dev/md0 /target/boot
   # sudo mount -t reiserfs /dev/md2 /target/tmp
   # sudo mount -t reiserfs /dev/md3 /target/usr
   # sudo mount -t reiserfs /dev/md4 /target/home
   # sudo mount -t reiserfs /dev/md5 /target/var
   # sudo mount -t reiserfs /dev/md6 /target/tools


Then I edited grub.conf where I changed all /dev/sda2 references to /dev/md1. This tells grub to boot from the raid

   # sudo gedit /target/boot/grub/grub.conf


Next I edited fstab to ensure the file system would mount from the raid

   # sudo gedit /target/etc/fstab &

fstab should look something similar to this:

# file system	mount point  	type    	options                  dump pass
/dev/md0     	/boot		ext3		defaults                0    2
/dev/md1	/		reiserfs	defaults	        0    1
/dev/sda5	none		swap   		sw,pri=1		0    0
#/dev/sdb5	none		swap   		sw,pri=1		0    0
proc		/proc         	proc    	defaults          	0    0
sys		/sys          	sysfs   	defaults		0    0

/dev/fd0        /mnt/floppy   	auto    	noauto,rw,sync,user,exec 0    0
/dev/hdb      	/mnt/cdrom    	iso9660 	noauto,ro,user,exec      0    0

/dev/md2        /tmp          	reiserfs	rw,nodev		0    2
/dev/md3        /usr          	reiserfs	rw,nodev		0    2
/dev/md4        /home         	reiserfs	rw,nosuid,nodev		0    2
/dev/md5        /var          	reiserfs	rw,nosuid,nodev		0    2
/dev/md6	/tools        	reiserfs	rw,nosuid,nodev		0    2


Finally, I created madam.conf to ensure the raid would be seen when I next re-booted

   # sudo gedit /target/etc/mdadm/mdadm.conf &

I added 'DEVICE partitions' to the top of mdadm.conf, then ran a scan to discover the array info

   # sudo mdadm --detail --scan

I added the output of the scan to mdadm.conf, saved and closed. 
After looking at various examples, I edited my mdadm.conf file (see below) - Apparently, newer versions of mdadm do not have 'devices' line but I added them in for safe measure:

DEVICE /dev/sda* /dev/sdb*
ARRAY /dev/md6 level=raid1 num-devices=2 UUID=31b60bca:5538bdb2:6e569818:d14416f5
   devices=/dev/sda10,/dev/sdb10
ARRAY /dev/md5 level=raid1 num-devices=2 UUID=7c52b2b2:c12f7cc8:bd3de03b:b6f3b68d
   devices=/dev/sda9,/dev/sdb9
ARRAY /dev/md4 level=raid1 num-devices=2 UUID=ac117ae9:ad2fdae2:1c97ef52:7d7f8282
   devices=/dev/sda8,/dev/sdb8
ARRAY /dev/md3 level=raid1 num-devices=2 UUID=68bfaf8c:03966140:ecb27083:19f61c68
   devices=/dev/sda7,/dev/sdb7
ARRAY /dev/md2 level=raid1 num-devices=2 UUID=b14de81c:5c125a31:61c04d12:5d8ec93a
   devices=/dev/sda6,/dev/sdb6
ARRAY /dev/md1 level=raid1 num-devices=2 UUID=59d458ed:6c2d0694:83a51bef:ac91f9df
   devices=/dev/sda2,/dev/sdb2
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=54858c51:11d376c4:60c1f89a:9dd88dee
   devices=/dev/sda1,/dev/sdb1


Another big problem I had was when I came to re-boot. On boot UBuntu checks each file system; however, now it will be checking the raid, not /dev/sda so it crashed out to a command line. I found this out the hard way - To fix it I ran:

   # sudo fsck -t ext3 /dev/md0
   # sudo reiserfsck --check /dev/md1
   # sudo reiserfsck --rebuild-sb /dev/md1
   # sudo reiserfsck --check /dev/md2
   # sudo reiserfsck --rebuild-sb /dev/md2
   # sudo reiserfsck --check /dev/md3
   # sudo reiserfsck --rebuild-sb /dev/md3
   # sudo reiserfsck --check /dev/md4
   # sudo reiserfsck --rebuild-sb /dev/md4
   # sudo reiserfsck --check /dev/md5
   # sudo reiserfsck --rebuild-sb /dev/md5
   # sudo reiserfsck --check /dev/md6
   # sudo reiserfsck --rebuild-sb /dev/md6


Once you have reached this stage it's time to shutdown, plug in the second drive, re-boot and cross your fingers. If you chose the 1st drive (DISC 0) to install to then the system will come straight up.

Once up and running I partitioned the second drive by copying the file system from sda using sfdisk

   # sudo sfdisk /dev/sda > sda.out
   # sudo sfdisk /dev/sdb < sda.out

(Check toggle 't' is fd)

Next I formatted the partitions with the correct file systems (I'm not sure if this step is necessary, however I'm sure it doesn't do any harm)

   # sudo mke2fs -j /dev/sdb1
   # sudo mkreiserfs /dev/sdb2
   # sudo mkswap /dev/sdb5
   # sudo mkreiserfs /dev/sdb6
   # sudo mkreiserfs /dev/sdb7
   # sudo mkreiserfs /dev/sdb8
   # sudo mkreiserfs /dev/sdb9
   # sudo mkreiserfs /dev/sdb10


I then re-booted to ensure the partitions were seen correctly 

The next step was to add the second disk to the mdadm raid

   sudo mdadm /dev/md0 -a /dev/sdb1
   sudo mdadm /dev/md1 -a /dev/sdb2
   sudo mdadm /dev/md2 -a /dev/sdb6
   sudo mdadm /dev/md3 -a /dev/sdb7
   sudo mdadm /dev/md4 -a /dev/sdb8
   sudo mdadm /dev/md5 -a /dev/sdb9
   sudo mdadm /dev/md6 -a /dev/sdb10

This step may take a while, you can watch the progress by typing # watch -n 6 cat /proc/mdstat

Do NOT re-boot whilst the drives are updating as corruption will occur. 

Once all of the partitions were synchronised, I updated mdadm.conf.

   sudo mdadm --detail --scan >> /etc/mdadm/mdadm.conf


Then I rebooted with a fresh install of UBuntu on a raid1. I am however unsure of how to check that the raid is actually updating without unplugging one of the drives, but for the time being I am happy with # cat /proc/mdstat



Issues:

Adding the second disc to the array - If sfdisk is not used and the partitions end up smaller than the original, you will get an error, similar to below when you come to add the new device.

mdadm: hot add failed for /dev/sdb2: No space left on device

To fix - Re-partition the drive and use sfdisk


Choosing the right disk - If you choose the wrong initial disc to install UBuntu to, when you come to re-boot, grub will not be found. To fix this I used Acronis (similar to ghost) to mirror my drive from sda to sdb, it was a lot of hassle! Make sure you choose the right disc!



Useful links:
[http://www.faqs.org/docs/Linux-HOWTO/Software-RAID-HOWTO.html](http://www.faqs.org/docs/Linux-HOWTO/Software-RAID-HOWTO.html)
[http://help.ubuntu.com/community/FakeRaidHowto](http://help.ubuntu.com/community/FakeRaidHowto)
[http://www.economysizegeek.com/category/linux/debian](http://www.economysizegeek.com/category/linux/debian)
[http://www200.pair.com/mecham/raid/raid1-degraded-lilo.html](http://www200.pair.com/mecham/raid/raid1-degraded-lilo.html)
[http://trinityhome.org/misc/bootable-raid1.html](http://trinityhome.org/misc/bootable-raid1.html)
[http://www.linuxsa.org.au/mailing-list/2003-07/1270.html](http://www.linuxsa.org.au/mailing-list/2003-07/1270.html)
[http://deb.riseup.net/storage/software-raid/](http://deb.riseup.net/storage/software-raid/)

There were a lot more of which I forgot to bookmark, but these definitely have some interesting info


Hope this is helpful to someone

Cheers, 
Adam

---

