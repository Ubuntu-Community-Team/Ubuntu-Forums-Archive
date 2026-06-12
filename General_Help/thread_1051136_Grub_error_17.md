---
title: "Grub error 17"
date: 2009-01-26
forum: General Help
---

### Post by Anders B on 2009-01-26
I've had a server running for a while now, but when i rebooted it yesterday it would'nt start. Instead i got a 'Error 17' when loading grub.

I searched these forums and found something called 'Super grub disk'. I tried using it, but i didnt work. ( Not sure if I used it correctly tho).

Then i made a Live CD, and booted from that. When i look at the partitions it says that my boot partition have an unknown filesystem.

Im reluctant to just format and reinstall ubuntu, because I have a forum and database on my machine (Yes, I should have made a backup. I know, im stupid :()

---

### Post by caljohnsmith on 2009-01-26
In order to get a clearer picture of your setup, how about booting your Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by Anders B on 2009-01-26
Sounds complicated.. Ill have a look at it tomorrow.

---

### Post by Anders B on 2009-01-27
Is this what you had in mind?


```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Boot file info:     
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x979b979b

Partition  Boot        Start          End         Size  Id System

/dev/sda1                 63  488,392,064  488,392,002   5 Extended
/dev/sda5                126  488,392,064  488,391,939  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders, total 240121728 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x25632562

Partition  Boot        Start          End         Size  Id System

/dev/sdb1    *            63  234,099,179  234,099,117  83 Linux
/dev/sdb2        234,099,180  240,107,489    6,008,310   5 Extended
/dev/sdb5        234,099,243  240,107,489    6,008,247  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda5: UUID="9fbdd456-07a4-477b-a7d0-aaf38ed4ecf8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: UUID="0794bdb3-d3ba-4a62-b597-ec88e03906bb" TYPE="swap" 
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

=========================== Unknown MBRs or Boot Sectors =======================

Unknown BootLoader  on sdb1

00000000  a4 81 00 00 00 00 00 00  be 6f 87 48 f1 1d 0c 49  |.........o.H...I|
00000010  f1 1d 0c 49 f1 1d 0c 49  00 00 00 00 00 00 00 00  |...I...I........|
00000020  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 60 a5 ad e6  00 00 00 00 00 00 00 00  |....`...........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  a4 81 00 00 00 00 00 00  be 6f 87 48 f1 1d 0c 49  |.........o.H...I|
00000090  f1 1d 0c 49 f1 1d 0c 49  00 00 00 00 00 00 00 00  |...I...I........|
000000a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000000e0  00 00 00 00 74 a5 ad e6  00 00 00 00 00 00 00 00  |....t...........|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  a4 81 00 00 00 00 00 00  be 6f 87 48 f1 1d 0c 49  |.........o.H...I|
00000110  f1 1d 0c 49 f1 1d 0c 49  00 00 00 00 00 00 00 00  |...I...I........|
00000120  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 75 a5 ad e6  00 00 00 00 00 00 00 00  |....u...........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  a4 81 00 00 00 00 00 00  be 6f 87 48 f1 1d 0c 49  |.........o.H...I|
00000190  f1 1d 0c 49 f1 1d 0c 49  00 00 00 00 00 00 00 00  |...I...I........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001e0  00 00 00 00 82 a5 ad e6  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200


=============================== StdErr Messages: ===============================

/dev/sdb1: unknown volume type
```

---

### Post by caljohnsmith on 2009-01-27
It looks like the problem is your sdb1 Linux partition is currently unreadable. How about trying:
```
sudo umount /dev/sdb1 && sudo fsck -yCM /dev/sdb1
```
And please post the output. If the fsck completes successfully, try:
```
sudo mount /dev/sdb1 /mnt && ls -l /mnt
```
And if that shows your sdb1 linux root directory, how about rebooting and let me know if you still get a Grub error 17.

---

### Post by Anders B on 2009-01-28
I tried 
```
sudo umount /dev/sdb1 && sudo fsck -yCM /dev/sdb1
```


This is what i get 

```
umount: /dev/sdb1: not mounted

```

Dont know if the fsck was succesful. It doesnt say anything.



When I try
```
sudo mount /dev/sdb1 /mnt && ls -l /mnt
```


I get
```
mount: special device /dev/sdb1 does not exist

```

---

### Post by caljohnsmith on 2009-01-28
OK, how about instead trying:
```
sudo fdisk -lu
```
Look for whichever is your linux partition (it was sdb1 before, but it might be the drive letters are changing), and then do:
```
sudo umount /dev/sdb1; sudo fsck -yCM /dev/sdb1
sudo mount /dev/sdb1 /mnt && ls -l /mnt
```
And replace "sdb1" in the above commands if your Linux partition is a different partition; please post the output of all the above commands.

---

### Post by Anders B on 2009-01-28
I fixed it myself. Thx anyway :D

---

