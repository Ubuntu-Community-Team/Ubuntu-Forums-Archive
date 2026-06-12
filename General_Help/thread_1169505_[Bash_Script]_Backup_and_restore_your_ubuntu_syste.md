---
title: "[Bash Script] Backup and restore your ubuntu system with &quot;live ubuntu backup&quot;"
date: 2009-05-25
forum: General Help
---

### Post by billbear on 2009-05-25
I wrote a bash script to backup the whole ubuntu system to a bootable squashfs file. I named it "lub.sh" ( live ubuntu backup) [COLOR=Red]
Update: New version that supports grub2 is at  #15,  Page 2.[/COLOR][]("http://ubuntuforums.org/showpost.php?p=8238906&postcount=15")
It's quite simple to use this script. 
Download and unzip the attachment, then allow execution of the script with this command:
sudo chmod +x /path/to/lub.sh
Next, install squashfs-tools and lupin-casper:
sudo apt-get install squashfs-tools lupin-casper

Now read the help with the command
/path/to/lub.sh -h
```
ubuntu@ubuntu-laptop:~$ lub.sh -h
live ubuntu backup, by billbear
This program can backup your running ubuntu system to a compressed, bootable squashfs 
file. When you want to restore, boot the squashfs backup and run this program again. 
You can also restore the backup to another machine. And with this script you can 
migrate ubuntu system on a virtual machine or a wubi installation to physical 
partitions.

Install:
Just copy this script anywhere and allow execution of the script. I put this script 
under /usr/local/bin, so that I don't have to type the path to this script everytime.

Use:
sudo /path/to/this/script -b
to backup or
sudo /path/to/this/script -r
to restore
You can also type
sudo bash /path/to/this/script -b
or
sudo bash /path/to/this/script -r

Note that
sudo sh /path/to/this/script -b
and
sudo sh /path/to/this/script -r
will not work.

Backup:
squashfs-tools is required for this program to backup your system. lupin-casper is 
required to make a bootable backup.
You can install them by typing
sudo apt-get install squashfs-tools lupin-casper
in a terminal.
Then you can backup your running ubuntu system by typing
sudo /path/to/this/script -b
If you put this script under /usr/local/bin, just type
sudo lub.sh -b
and follow the instructions.
You can specify where to save the backup, files/folders you want to exclude from the 
backup.
You don't need to umount external media, windows partitions, or any manually mounted 
partitions. They will be automatically ignored. Therefore you can save the backup to 
external media, windows partitions, etc.
Waring: You must make sure you have enough space to save the backup.
The program will generate other files needed for booting the backup. Read the menu.lst 
file the program generated under the backup folder for details on how to boot the 
backup.

Restore:
Read the menu.lst file the program generated under the backup folder for details on 
how to boot the backup.
After booting into the live ubuntu backup, open a terminal and type
sudo /path/to/this/script -r
If you have put this script under /usr/local/bin when backup, now just type
sudo lub.sh -r
and follow the instructions.
Note: This program does not provide a partitioner (it can only format partitions 
but cannot create, delete, or resize partitions). The backup can be restored to 
existing partitions. So it is recommended that you include gparted in the backup. 
And if the partition table has any error, you will not be able to restore the 
backup until the errors are fixed.
You can specify partitions and mount points, if you have no swap partition, 
the program will make a swap file for you if you tell it to do so.
It will generate new fstab and install grub. It can also change the hostname,
username and password if you tell it to do so.


```Backup your running ubuntu with 
sudo /path/to/lub.sh -b
```
ubuntu@ubuntu-laptop:~$ sudo lub.sh -b
[sudo] password for ubuntu: 
You are about to backup your system. It is recommended that you quit all open 
applications now. Continue?(y/n)
y
Specify an empty directory(absolute path) to save the backup. You can drag directory 
from Nautilus File Manager and drop it here. Feel free to use external media.
If you don't specify, the backup will be saved to /home/ubuntu/backup-05242009

Specify the files/folders you want to exclude from the backup, one file/folder per line. 
You can drag and drop from Nautilus. End with an empty line.

Start to backup?(y/n)
y
Parallel mksquashfs: Using 1 processor
Creating little endian 3.1 filesystem on /home/ubuntu/backup-05242009/backup05242009.squashfs, block size 131072.
[=========================================================== ] 92923/93026  99%
File /tmp/bind/var/log/ConsoleKit/history changed size while reading filesystem, attempting to re-read
[=========================================================== ] 92928/93026  99%
File /tmp/bind/var/log/auth.log changed size while reading filesystem, attempting to re-read
[=========================================================== ] 92935/93026  99%
File /tmp/bind/var/log/daemon.log changed size while reading filesystem, attempting to re-read
[=========================================================== ] 92996/93026  99%
File /tmp/bind/var/log/messages changed size while reading filesystem, attempting to re-read
[=========================================================== ] 93000/93026  99%
File /tmp/bind/var/log/syslog changed size while reading filesystem, attempting to re-read
[============================================================] 93026/93026 100%
Exportable Little endian filesystem, data block size 131072, compressed data, 
compressed metadata, compressed fragments, duplicates are removed
Filesystem size 789662.29 Kbytes (771.15 Mbytes)
    40.17% of uncompressed filesystem size (1965650.60 Kbytes)
Inode table size 1155381 bytes (1128.30 Kbytes)
    29.20% of uncompressed inode table size (3957359 bytes)
Directory table size 1113959 bytes (1087.85 Kbytes)
    47.00% of uncompressed directory table size (2370240 bytes)
Number of duplicate files found 8349
Number of inodes 115898
Number of files 87874
Number of fragments 6597
Number of symbolic links  14964
Number of device nodes 95
Number of fifo nodes 3
Number of socket nodes 35
Number of directories 12927
Number of uids 14
    root (0)
    syslog (101)
    ubuntu (1000)
    daemon (1)
    polkituser (109)
    libuuid (100)
    lp (7)
    man (6)
    avahi-autoipd (104)
    gdm (105)
    news (9)
    messagebus (108)
    hplip (103)
    klog (102)
Number of gids 29
    video (44)
    audio (29)
    tty (5)
    kmem (15)
    disk (6)
    adm (4)
    daemon (1)
    dip (30)
    lp (7)
    fuse (104)
    shadow (42)
    ssl-cert (105)
    messagebus (117)
    crontab (107)
    mail (8)
    lpadmin (106)
    mlocate (108)
    utmp (43)
    ssh (109)
    games (60)
    polkituser (118)
    root (0)
    staff (50)
    libuuid (101)
    src (40)
    admin (121)
    avahi-autoipd (110)
    gdm (111)
    klog (103)
Your backup is ready in /home/ubuntu/backup-05242009. 
Please read the menu.lst inside :)

```Take a look at the backup:
```
ubuntu@ubuntu-laptop:~$ ls /home/ubuntu/backup-05242009/
backup05242009.squashfs       menu.lst
initrd.img-2.6.28-11-generic  vmlinuz-2.6.28-11-generic

```Read the menu.lst to learn how to boot the backup file:
```
ubuntu@ubuntu-laptop:~$ cat /home/ubuntu/backup-05242009/menu.lst 
# This menu.lst is for grub4dos only. You must edit it to use with gnu grub


# Instructions to boot your backup05242009.squashfs directly on a windows PC:
# Download the latest grub4dos from http://download.gna.org/grub4dos
# Unzip grub4dos, then copy grldr and grldr.mbr to the root of your c: drive
# Also copy this menu.lst to the root of your c: drive
# Then make a directory "casper" under the root of any partition and copy 
backup05242009.squashfs, initrd.img-2.6.28-11-generic, vmlinuz-2.6.28-11-generic 
to the directory
# Then add this line to boot.ini (without #)
# c:\grldr.mbr="grub4dos"
##### On Windows Vista, you can still create a boot.ini yourself with these lines:
##### [boot loader]
##### [operating systems]
##### c:\grldr.mbr="grub4dos"
# Reboot and select grub4dos


# Instructions to boot your backup05242009.squashfs directly on a linux PC:
# Make a directory "casper" under the root of any partition (Note that NTFS is not 
readable by gnu grub so don't put casper there) and copy backup05242009.squashfs, 
initrd.img-2.6.28-11-generic, vmlinuz-2.6.28-11-generic to the directory
# Then copy the Live Ubuntu Backup entries below to the end of your /boot/grub/menu.lst
file and change the "find --set-root" line to "root (hd?,?)" (where you created the 
directory "casper")


default    0
timeout 10

title Live Ubuntu Backup 05242009
find --set-root /casper/vmlinuz-2.6.28-11-generic
kernel /casper/vmlinuz-2.6.28-11-generic boot=casper ro ignore_uuid
initrd /casper/initrd.img-2.6.28-11-generic

title Live Ubuntu Backup 05242009, Recovery Mode
find --set-root /casper/vmlinuz-2.6.28-11-generic
kernel /casper/vmlinuz-2.6.28-11-generic boot=casper ro single ignore_uuid
initrd /casper/initrd.img-2.6.28-11-generic

```Tip: You can save your backup on an external HD and boot it on different machines.

After booting the live ubuntu backup, run this command to restore (or install) your backup:
sudo /path/to/lub.sh -r
```
ubuntu@ubuntu:~$ sudo lub.sh -r
This will restore your backup. Continue? (y/n)
y
Specify the squashfs backup file (absolute path). You can drag the file from Nautilus 
File Manager and drop it here. If you are booting from the backup squashfs, you can 
just hit enter, and the squashfs you are booting from will be used.

Which partition do you want to use as / ?
1) /dev/sda1 ntfs  5198MB  5) /dev/sda7 swap  625MB
2) /dev/sda10 swap  280MB  6) /dev/sda8 ext4  1464MB
3) /dev/sda5 ext4  206MB   7) /dev/sda9 swap  1291MB
4) /dev/sda6 ext4  6087MB  8) /dev/sdb1 vfat  8015MB
#? 4
You selected /dev/sda6, it currently contains these files/directories:
bin    cdrom  home       lost+found  opt   sbin     sys  var
boot    dev    initrd.img  media       proc  selinux  tmp  vmlinuz
casper    etc    lib       mnt           root  srv      usr
confirm?(y/n)
y
Do you want to format this partition?(y/n)
y
Format /dev/sda6 as:
1) ext2
2) ext3
3) ext4
4) reiserfs
5) jfs
6) xfs
#? 4
Which partition do you want to use as swap ?
 1) /dev/sda1 ntfs  5198MB
 2) /dev/sda10 swap  280MB
 3) /dev/sda5 ext4  206MB
 4) 
 5) /dev/sda7 swap  625MB
 6) /dev/sda8 ext4  1464MB
 7) /dev/sda9 swap  1291MB
 8) /dev/sdb1 vfat  8015MB
 9) None
10) None and finish setting up partitions
#? 7
You selected /dev/sda9, it currently contains these files/directories:
confirm?(y/n)
y
/dev/sda9 will be formatted as swap.
Which partition do you want to use as /home ?
 1) /dev/sda1 ntfs  5198MB
 2) /dev/sda10 swap  280MB
 3) /dev/sda5 ext4  206MB
 4) 
 5) /dev/sda7 swap  625MB
 6) /dev/sda8 ext4  1464MB
 7) 
 8) /dev/sdb1 vfat  8015MB
 9) None
10) None and finish setting up partitions
#? 6
You selected /dev/sda8, it currently contains these files/directories:
billbear  lost+found
confirm?(y/n)
y
Do you want to format this partition?(y/n)
y
Format /dev/sda8 as:
1) ext2
2) ext3
3) ext4
4) reiserfs
5) jfs
6) xfs
#? 5
Which partition do you want to use as /boot ?
 1) /dev/sda1 ntfs  5198MB
 2) /dev/sda10 swap  280MB
 3) /dev/sda5 ext4  206MB
 4) 
 5) /dev/sda7 swap  625MB
 6) 
 7) 
 8) /dev/sdb1 vfat  8015MB
 9) None
10) None and finish setting up partitions
#? 3
You selected /dev/sda5, it currently contains these files/directories:
abi-2.6.28-11-generic          memtest86+.bin
config-2.6.28-11-generic      System.map-2.6.28-11-generic
grub                  vmcoreinfo-2.6.28-11-generic
initrd.img-2.6.28-11-generic  vmlinuz-2.6.28-11-generic
lost+found
confirm?(y/n)
y
Do you want to format this partition?(y/n)
y
Format /dev/sda5 as:
1) ext2
2) ext3
3) ext4
4) reiserfs
5) jfs
6) xfs
#? 4
Which partition do you want to use as /tmp ?
 1) /dev/sda1 ntfs  5198MB
 2) /dev/sda10 swap  280MB
 3) 
 4) 
 5) /dev/sda7 swap  625MB
 6) 
 7) 
 8) /dev/sdb1 vfat  8015MB
 9) None
10) None and finish setting up partitions
#? 10
Start to format partitions (if any). Continue? (y/n)
y
Formatting /dev/sda6
mkfs.reiserfs 3.6.19 (2003 www.namesys.com)

Done

Formatting /dev/sda8
Done

Formatting /dev/sda5
mkfs.reiserfs 3.6.19 (2003 www.namesys.com)

Done

If you have other partitions for the target system, open another terminal and mount 
them to appropriate places under /tmp/target. Then press return.

Specify the place into which you want to install GRUB stage1.
/dev/sda and /dev/sda5 are recommended.
1) /dev/sda,MBR           5) /dev/sda6,reiserfs     9) /dev/sdb1,vfat
2) /dev/sdb,MBR           6) /dev/sda7,swap        10) none,not_recommended
3) /dev/sda10,swap       7) /dev/sda8,jfs
4) /dev/sda5,reiserfs       8) /dev/sda9,swap
#? 1
The restore process will launch. Continue?(y/n)
y
......
......
Enter new hostname or leave blank to use the old one
old hostname: ubuntu-laptop
new hostname:
billbear-pc
Do you want to change the name of user ubuntu? (y/n)
y
new username:
billbear
Do you want to change the password of user billbear? (y/n)
y
Enter new UNIX password: 
Retype new UNIX password: 
passwd: password updated successfully
If the password was not successfully changed, now you have another chance to change it.
Do you want to change the password of user billbear again? (y/n)
n
Done! Enjoy:)

```

---

### Post by billbear on 2009-05-30
I modified the script, added these features:
can optionally exclude all user files under /home
can optionally exclude the local repository of retrieved package files in /var/cache/apt/archives/ 
can restore to a partition without a uuid
can check for duplicate UUIDs

Now it's version 1.1.1

Tested on ubuntu 9.04, kubuntu 9.04, xubuntu 9.04, ubuntu server 9.04

---

### Post by vishy1618 on 2009-05-30
This is simply superb! Nice work buddy! You seem to have put a lot of hard work into this. Thanks for sharing!

---

### Post by billbear on 2009-05-31
Version 1.2, minor modifications.

---

### Post by yatot on 2009-06-02
would this work on a particular file of a particular user on a particular schedule?

thanks.

---

### Post by billbear on 2009-06-02
> **yatot said:**
> would this work on a particular file of a particular user on a particular schedule?

thanks.

Sorry,I don't quite understand.

---

### Post by jenkinbr on 2009-06-03
I have to say that this looks very interesting - I may just have to try it!

---

### Post by RobertL on 2009-06-06
I would like to use this but I'm afraid to try it without fully understanding what it's doing. 

1) Could you explain "probe_partitions"? In particular, what are the size=xxxx lines doing and why do they contain a comment with non-western characters? Do I have a garbled version of it? Here is what I have:

probe_partitions(){
    for i in /dev/[hs]d[a-z][0-9]*; do
    vol_id $i > /dev/null 2>&1 || continue
    parted -s $i print > /dev/null 2>&1 || continue
    part[${#part
[*]}]=$i
    oldfstype[${#oldfstype
[*]}]=`vol_id --type $i`
    size=`parted -s $i print | grep $i`
    size=${size#*:}
    size=${size#*&#65306;}    #&#20840;&#35282;&#20882;&#21495;&#65292;&#21488;&#28286; parted &#36755;&#20986;&#29992;&#36825;&#20010; :(
    partinfo[${#partinfo
[*]}]="$i `vol_id --type $i` $size"
    done
}

2) Do you modify the running system in any way? I'm concerned that if something fails to work I'll be left with a damaged system. (not likely but I'd like assurance). For example, what is the following line is doing?:

rm $exclude

I see that lots of work goes into building $exclude but I hope this isn't removing a bunch of directories under the assumption that they aren't needed or will be recreated.

I know my questions result from my ignorance of bash programming but I'm trying to learn. I'd like to use this script with confidence so if you would be kind enough to take the time to explain these point I'd be grateful.

---

### Post by billbear on 2009-06-08
1) 
probe_partitions(){ #Generates a list of recognizable partitions
for i in /dev/[hs]d[a-z][0-9]*; do
vol_id $i > /dev/null 2>&1 || continue #Bypass unrecognizable partitions and extended partition
parted -s $i print > /dev/null 2>&1 || continue #If a partition table has errors, don't list the partitions of that disk, avoid further damages to the partition table
part[${#part[*]}]=$i #Save partition device name to array part[]
oldfstype[${#oldfstype[*]}]=`vol_id --type $i` ##Save partition file system to array oldfstype[]
size=`parted -s $i print | grep $i` #Like this -- Disk /dev/sda1: 12.0GB
size=${size#*:} # Remove "Disk /dev/sda1:" and now size=12.0GB
size=${size#*&#65306;} #If locale=TAIWAN, parted outputs Chinese colon "&#65306;" rather than English colon ":". The comment was written in Chinese because this is a Chinese problem only.
partinfo[${#partinfo[*]}]="$i `vol_id --type $i` $size" #Like this -- /dev/sda1 ext3 12.0GB
done
}

2)Do you modify the running system in any way? No, except that it requires that you install squashfs-tools and lupin-casper by "sudo apt-get install squashfs-tools lupin-casper".
$exclude is a temporary file this script creates under /tmp that lists files needed to be excluded from the backup, such as /boot/grub, /etc/fstab (When restoring you may use a completely different partition scheme so these files must be rebuilt), backup file itself, lost+found in every partition, swap files if any, /tmp, and user defined excluded files.  When backup finishes, rm $exclude removes that temporary file. In fact all the files under /tmp are removed upon every reboot, so if you really worry about "rm $exclude" you can just delete this line.

---

### Post by RobertL on 2009-06-09
Thanks for the explanations. That's a really cool script! I'm ready to use it for backup but I'm still not sure I'm ready for the acid test -- format the boot drive and hope to restore. Maybe after I read it three more times I'll be bold enough :)

---

### Post by Shikaku2 on 2009-06-14
[FONT=System]I love this program.  It worked very well for me, but probably not for what you intended.  I cloned a machine using this program :grin: but I will be using it for backing up as well.  Thank you very much!
[/FONT]

---

### Post by billbear on 2009-06-16
Yes you can use the script to clone a machine to another. 
A special use is to migrate ubuntu from a virtual machine to physical machines. I set up 9.04 on a virtual machine and cloned it to all my PCs, Macs, and Notebooks.
It can also migrate a wubi installation to physical partitions.

---

### Post by crownedzero on 2009-10-20
I'll have to give this a shot.

Have you made any other changes to it recently?

---

### Post by Shikaku2 on 2009-11-02
I wonder if this needs updating for Karmic?

---

### Post by billbear on 2009-11-04
> **Shikaku2 said:**
> I wonder if this needs updating for Karmic?

Yes version 2.2 is below

---

### Post by Shikaku2 on 2009-11-10
Note: installing lupin-casper enables compcache on your computer, and it should be disabled because if you use a lot of your RAM it can cause stability issues and is meant only for the LiveCD.

Run this to disable it:

sudo rm /usr/share/initramfs-tools/conf.d/compcache && sudo update-initramfs -u

And reboot or run sudo swapoff /dev/ramzswap0

---

### Post by billbear on 2009-11-11
Thank you for your comment Shikaku, though I have not encountered problems with lupin-casper installed and do not quite understand why this should cause stability issues.

---

### Post by MerlinW on 2010-01-25
Thanks, it's a great script :popcorn:

---

### Post by littleconda on 2010-02-05
Thank You,\\:D/
Just wanted to keep this post alive and say thank you!  I was looking for a solution to move my Karmic Install  from a 750Gb HDD to a 500GB HDD, (only had about 300GB used), something that was not possible with dd or imaging software like Clonezilla.   This thing worked FANTASTIC.
It allowed me to back up my live file system (keep my current system running) and then restore to an external drive (while current system was running).  I then swapped the external drive for the internal (running) drive and rebooted, all went well!!  Only additional step was to recreate the symbolic link to my second internal drive and fix the fstab. 

Oh, did i forget to say Thank You!

---

### Post by rcarlisle on 2010-02-22
Just saying thanks for this nice piece of work. I am currently making a backup with it and will be performing a test restore to a blank drive I have laying around. 
Will post back, but no issues so far. 
This was exactly the type of solution I was looking for!
Thanks again.

---

### Post by milkyspit on 2010-03-14
I have a little different need than most folks... I'm running a home file server that's got Hardy installed (64bit)... the hard drive has both the operating system and a large fileserver repository. I backup to external hard drive weekly and rotate a couple drives for the backups. Goal is to capture everything on the external drive, keep permissions intact, compress to save some space on the external drive, and most importantly, allow me to grab individual files from the backup if I need something later. Looks like this script will give me all that. I'm going to give it a try. Thanks!

---

### Post by westforest on 2010-05-01
Can I restore my system without having to boot into the backup system? Say I want to switch my laptop's drive X to an SSD drive Y, but I don't have an external drive. I plug both to my desktop machine with drive Z, and I want to back up X to drive Z, and then restore to the SSD drive Y. Is this possible?

---

### Post by billbear on 2010-05-07
LUB backs up the currently running system. If you do backup on your desktop, it backs up the running ubuntu of the desktop, not drive X of your laptop. You must do backup on the laptop and transfer the file to your desktop.
You can restore without having to boot into the backup system. You can restore from another ubuntu of the same version, or a livecd environment of the same version, just specify the path of your backup.

---

### Post by m4cph1sto on 2011-05-10
I just discovered this script and it looks wonderful!  Do you think it would work for backing up non-Ubuntu linux installations as well?  I have a laptop with Ubuntu 10.10, another with a non-Ubuntu Debian based distro, and another based on Fedora 14.  Thanks for your work developing this - I think more people should know about it!

---

### Post by RollerCOM on 2011-09-29
Here we go :) I'm giving it my best shot so i can switch from my crappy old ATA 160 gb to a brand new SATA :)

---

### Post by N4RPS on 2011-10-06
Hello, All.

Hallelujah! :D

Thank you, for creating this script. Having tried several other utilities to back up my Linux installation, this is the first one to have produced a backup that restored things successfully. 

For those who say it isn't so, people learning Linux are going to do something that requires an ability to backup and restore their installations. Unfortunately, most all of these utilities seem to require a better understanding of what is to be included and excluded in backups than I currently have.

These are the issues I encountered, but then again, this script is based on a GRUB and a release of Ubuntu that is prior to mine: 

I tried to partition & format the restore target using the  script, but was unsuccessful. This may have to do with my using a 16GB SDHC card to run Linux. 

I think the error had to with some kind of mounting issue, perhaps, but gparted on the LiveCD took care of the partitioning and formatting.

It wanted to default to sda and I needed sdb, so I modded the script to start searching at sdb instead.

Again, thank you for your extensive efforts to make system archiving as painless as possible for the Linux community.

73 DE N4RPS
Rob

---

