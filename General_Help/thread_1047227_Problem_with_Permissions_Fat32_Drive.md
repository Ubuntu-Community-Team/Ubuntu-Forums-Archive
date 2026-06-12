---
title: "Problem with Permissions Fat32 Drive"
date: 2009-01-22
forum: General Help
---

### Post by bob-linux-user on 2009-01-22
I am running Intrepid in a dual boot system with Windows XP. All my documents including my Firefox and Thunderbird Profiles are on a shared FAT 32 partition so I can access my files from either OS and also read emails/surf the net from either the Linux or windows versions of Firefox or Thunderbird. 

The problem I have is that often when I boot in Ubuntu I try to use Firefox or Thunderbird and then find I can't because it says that they are already running. When I look at the Profiles in Nautilus it says I do not have permission and puts the padlock emblem on them. I have tried changing the permissions and as a last resort I have created a log on for root ( I know this is not a very good idea) and tried reading emails/surfing the net from there. This sometimes works but I now find that I am getting the same problem even running in root.

This is intensely irritating as even logging out does not solve the problem- I have to reboot the PC.

I have also thought of another solution which is far from ideal- put the mobile Windows versions of Firefox and Thunderbird on the same FAT 32 and run them from Windows and also run them from Ubuntu via WINE.

Has anyone another solution please? Is there a command which will give me absolute and complete control over ALL my files (presumably while running in root)? Is it a problem with the way Ubuntu reads FAT32 partitions-often the error messages say "read only filesystem"? 

?

---

### Post by taurus on 2009-01-22
Did you mount that fa32/vfat partition through /etc/fstab?  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by bob-linux-user on 2009-01-22
Thanks Taurus

Please see results below, running as myself (not root). When I set the system I did not edit any files, but created/edited the existing partitions using the partition editor on the live CD. Some time later I slid the FAT32 partition along and expanded it the same way. BTW the  "Kingston" referred to is my USB key- I don't know why it shows up here as it was not even physically attached to the PC when I turned it on.Results follow:-


bob@bob-desktop:~$ sudo fdisk -l
[sudo] password for bob: 

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ea02e9f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1965    15783831    7  HPFS/NTFS
/dev/sda2            1966        3515    12450375   83  Linux
/dev/sda3            3516        3579      514080   82  Linux swap / Solaris
/dev/sda4            3580        4865    10329795    b  W95 FAT32
bob@bob-desktop:~$ sudo blkid
/dev/sda1: UUID="3CE3A70639FBE450" TYPE="ntfs" 
/dev/sda2: UUID="bd9fe265-2a73-43af-8617-2dadb5cf1b67" TYPE="ext3" 
/dev/sda3: TYPE="swap" UUID="4eb82bfa-7e0f-4973-8e89-1ad352916066" 
/dev/sda4: UUID="48A8-AD0F" TYPE="vfat" 
/dev/sdb1: LABEL="KINGSTON" UUID="90C2-14F5" TYPE="vfat" 
bob@bob-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=bd9fe265-2a73-43af-8617-2dadb5cf1b67 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=4fd57c55-d642-4d62-8869-545cecd7cc88 none            swap    sw              0       0
/dev/scd2       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
bob@bob-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              12G  9.9G  1.2G  90% /
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M  208K 1012M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  2.9M 1010M   1% /dev
tmpfs                1013M  344K 1012M   1% /dev/shm
lrm                  1013M  2.0M 1011M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/scd2             4.1G  4.1G     0 100% /media/cdrom0
/dev/sda4             9.9G  6.4G  3.6G  65% /media/disk
bob@bob-desktop:~$

---

### Post by taurus on 2009-01-22
Open a terminal and edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
UUID=48A8-AD0F   /media/sda4   vfat   iocharset=utf8,umask=000  0  0
```
Save it and close gedit editing window.  Now, create a new mount point for /dev/sda4.

```
sudo mkdir /media/sda4
```
Reboot and your /dev/sda4 now is mounted to /media/sda4.

---

### Post by penC on 2009-01-22
> **bob-linux-user said:**
> 
Has anyone another solution please? Is there a command which will give me absolute and complete control over ALL my files (presumably while running in root)? Is it a problem with the way Ubuntu reads FAT32 partitions-often the error messages say "read only filesystem"? 

?

Bob,

  you should have a complete control over the files without any tricks when using FAT32. What makes me worry is the message about "read-only filesystem". If I were you I would boot the Windows and run chkdsk (or whatever disk repair command is available); I fear you have bad sectors in your FAT32 partition. Propably not real (physical) ones, but real enough for the VFAT driver.

Good luck,

  pen

---

### Post by bob-linux-user on 2009-01-23
Thanks to Taurus and PenC

I ran diskchk from Windows and it did not find any errors.

Followed all of Taurus' advice above and also altered the appropriate profiles.ini files so the programs were looking in the right places. 

It seems to be running ok at the moment although I seem to have lost some firefox add ins which is no great problem.

Thanks

---

### Post by bob-linux-user on 2009-02-04
I seem to have "spoken" too soon earlier. The problem has happened again. I get problems with either firefox or thunderbird saying they are running already and not therefore not starting, or problems with thunderbird address book saying it is read only or saying it cannot save drafts or move a sent email into the sent folder. I have also seen padlock emblems appear on all the folders on my FAT32 partition. 

When running in XP I noticed that the drive was heavily fragmented so I defragged it in case this made any difference. It didn't.

I get the problems when logged in as root and as myself.

Is the problem anything to with parentlock files which seem to appear? I found I could not delete these even when running as root.

Any ideas anyone please? I don't want to go back to Windows to surf or read emails.

I had another idea-if the problem was caused by FAT32-set the PC up so that there are only 3 partitions :-
Windows NTFS
Ubuntu EXT2 (not EXT3)
swap

and then put all my documents and profiles on the Ubuntu partition (in documents) and install the EXT2 driver in Windows so XP can access the documents and profiles as well.

Is that a good idea?

---

### Post by mb_webguy on 2009-02-04
FAT32 and ntfs filesystems can't handle Linux-style file permissions, and are mounted with one set of file permissions for the entire filesystem.  By default, they are mounted with owner and group both set as root, and read-only (and possibly execute, but I'm not sure) permissions for everyone.

If you made the change to fstab that taurus suggested, *then remounted everything* using "sudo mount -a" (or rebooted), then the drive will be mounted with full read/write/execute permissions, though still owned by root.  You can change the owner and group as well with the options "UID=nnnn" where nnnn is the user id, and "GID=nnnn" where nnnn is the group id.

---

### Post by bob-linux-user on 2009-02-04
Thanks mb_webguy for the info. I am not actually sure how to do what you suggest as I am a relative newbie (and it is the file permissions which is the thing I find hardest after using Windows). I won't try it at the moment anyway as I have noticed that Firefox and Thunderbird usually work ok if I display the drive in nautilus first before trying to start the applications. I am not sure if this "usually" is "always" so may post here again in the near future. Thanks

---

### Post by AR_Kozz on 2009-03-29
this has been kind driving me nuts too. I have a similar problem except that for me, it's not any problem of access, it's that after I upgraded to Hardy from Gutsy, linux seems to insists my fat-32 formatted hard drive is read-only. Combined with that, it now auto-mounts it as read-only, where before it would just leave it be and let me do the mounting. If I unmount it and do the terminal work before it decides to grab it again, I can convince it - for a while, at least - that it's not really read-only. I think these lines from the system log may be to that effect:

Mar 29 04:43:35 frankenstein kernel: [  337.366572] sd 3:0:0:0: [sdc] 490234752 512-byte hardware sectors (251000 MB)
Mar 29 04:43:35 frankenstein kernel: [  337.373580] sd 3:0:0:0: [sdc] Test WP failed, assume Write Enabled

after mounting the drive I can start writing with root commands... for about 10 minutes. Usually I can write about 700 mb in that amount of time; anything bigger to write, and at around 10 minutes the operation is interrupted by (for a dvd in this example)

cp: cannot create regular file `/home/dan/Desktop/usbdrive/video/dvd/VIDEO_TS/VIDEO_TS.BUP': Read-only file system
cp: cannot create regular file `/home/dan/Desktop/usbdrive/video/dvd/VIDEO_TS/VTS_01_1.VOB': Read-only file system
cp: cannot create regular file `/home/dan/Desktop/usbdrive/video/dvd/VIDEO_TS/VTS_01_2.VOB': Read-only file system
cp: cannot create regular file `/home/dan/Desktop/usbdrive/video/dvd/VIDEO_TS/VTS_01_0.IFO': Read-only file system
cp: cannot create regular file `/home/dan/Desktop/usbdrive/video/dvd/VIDEO_TS/VIDEO_TS.IFO': Read-only file system
cp: cannot create regular file `/home/dan/Desktop/usbdrive/video/dvd/VIDEO_TS/VTS_01_0.BUP': Read-only file system
cp: cannot create regular file `/home/dan/Desktop/usbdrive/video/dvd/VIDEO_TS/VTS_01_3.VOB': Read-only file system

leaving about 700mb of VTS_01_4.VOB on the usb drive, and nothing else but the dvd folders.

Since the drive worked perfectly under Gutsy, I kind of suspect that Gnome is periodically trying to jump in and remount the drive as read-only (I've caught it doing this at least once) or else allowing my root privilege to expire.

Either way, hell of annoying. My ps3 can still write to the drive so I know it doesn't have errors.

---

