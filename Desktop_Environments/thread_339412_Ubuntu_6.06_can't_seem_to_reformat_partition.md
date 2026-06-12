---
title: "Ubuntu 6.06 can't seem to reformat partition"
date: 2007-01-15
forum: Desktop Environments
---

### Post by zerosystem on 2007-01-15
This is my first experience with Linux, let alone any other distro. I'm having with a partition, that was originally formatted as ntfs.

I initially used a GParted cd to use the partition edit to manually create partitions for Ubuntu, prior to installing it. When I did install Ubuntu, I selected the partitions instead of creating them during the install. As it appears in the partition list in Disks Manager, I have 3 partitions, 1 for a swap disk, which appears as /dev/hda1 and is 5gb, the 2nd one is one for a main Ubuntu install formated as ext3, which appears as /dev/hda6 and is 28gb, and the last partition is the one I'm having trouble with.

It was originally NTFS (because I had it before I installed Ubuntu) and 79gb, and after I copied some personal files off the partition, I used the GParted cd again to delete and reformat the partition as ext3, and when I rebooted into Ubuntu, the drive reappeared as a blank partiton, named "79.0 GB Volume", but I could not access it because I couldn't mount it. 

The error says 

"Unable to mount the selected partition. Mount: only root can mount /dev/hda5 on /media/hda5"

I went into Disks Manager, and clicked "enable" for /dev/hda5, but nothing happened.

After Googling around for answers I tried the following command:

sudo mount /dev/hda5

I entered my password, but the following appeared:

mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

After trying "dmesg | tail", the following appeared:

[17179613.316000] Bluetooth: L2CAP ver 2.8
[17179613.316000] Bluetooth: L2CAP socket layer initialized
[17179613.372000] Bluetooth: RFCOMM socket layer initialized
[17179613.372000] Bluetooth: RFCOMM TTY layer initialized
[17179613.372000] Bluetooth: RFCOMM ver 1.7
[17179684.504000] Warning: /proc/ide/hd?/settings interface is obsolete, and wil l be removed soon!
[17179685.056000] EXT2-fs warning (device hda5): ext2_fill_super: mounting ext3 filesystem as ext2
[17179732.316000] NTFS-fs error (device hda5): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179732.316000] NTFS-fs error (device hda5): read_ntfs_boot_sector(): Mount op tion errors=recover not used. Aborting without trying to recover.
[17179732.316000] NTFS-fs error (device hda5): ntfs_fill_super(): Not an NTFS vo lume.

I tried "dmesg | tail" again, and a slightly different message appeared:

[17181379.924000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=60.12.194.5 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=UDP SPT=43599 DPT=1026 LEN=467
[17181610.840000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=24.40.7.117 DST=154.20.180.149 LEN=674 TOS=0x00 PREC=0x00 TTL=118 ID=20461 PROTO=UDP SPT=31315 DPT=1026 LEN=654
[17181804.296000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=221.12.113.246 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=56742 DPT=1026 LEN=467
[17181804.300000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=221.12.113.246 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=56744 DPT=1027 LEN=467
[17181974.220000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=221.12.113.251 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=51533 DPT=1026 LEN=467
[17181974.224000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=221.12.113.251 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=51533 DPT=1027 LEN=467
[17182029.596000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=202.97.238.199 DST=154.20.180.149 LEN=485 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=36902 DPT=1027 LEN=465
[17182139.188000] NTFS-fs error (device hda5): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17182139.188000] NTFS-fs error (device hda5): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17182139.188000] NTFS-fs error (device hda5): ntfs_fill_super(): Not an NTFS volume.

The impression I'm getting from these messages are that the filesystem for /dev/hda5 is invalid. When I boot into GParted, It shows the partition as the last filesystem I last tried to  format it as, and having GParted check the filesystem yielded nothing, either. When I boot into Ubuntu, the partition always appears as "Windows NTFS", and the formatter in Disks Manager doesn't do anything either, it stays as Windows NTFS.

I'd appreciate any help, as I'm running out of space on my Ubuntu partition (I have 80mb left!) and I don't really have the option to buy another hard drive.

---

### Post by kebes on 2007-01-15
In a terminal, type this:
```

more /etc/fstab

```

It will list the defined volume mountpoints. You'll see something like this:

```

$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       none            swap    sw              0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/other     ntfs    defaults        0       2
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Check the line for this other drive you're trying to mount... (the line that says "/dev/hda5")... it probably says "ntfs" but it should say "ext3". (When you installed Ubuntu it was NTFS I guess, and it has not been updated.)

You can fix the file manually by using any text editor, so on a commandline type:
```

sudo nano /etc/fstab

```

("sudo" means "do this as superuser" and "nano" is a text editor). Once the editor is open, go to the line and change it to "ext3" like I said. Then go Ctrl+X to exit, and say "yes" to saving changes.

Once the file is fixed, try rebooting (or going "sudo mount -a" on commandline) and see if it's now fixed. If not, post back whatever information you've got (like the contents of fstab) and we'll try to help.


P.S.: Welcome to Linux! I hope you find it fun...

---

### Post by zerosystem on 2007-01-15
It seems to have not worked... I still can't mount it, and Disks Manager's enable button does nothing. However, the filesystem is now ext3.

dmesg | tail reveals:

```
[17179717.076000] EXT3-fs: mounted filesystem with ordered data mode.
[17179722.736000] EXT3-fs: Unrecognized mount option "nls=utf8" or missing value
[17179817.684000] kjournald starting.  Commit interval 5 seconds
[17179817.688000] EXT3 FS on hda5, internal journal
[17179817.688000] EXT3-fs: mounted filesystem with ordered data mode.
[17179824.856000] EXT3-fs: Unrecognized mount option "nls=utf8" or missing value
[17179827.424000] EXT3-fs: Unrecognized mount option "nls=utf8" or missing value
[17179844.928000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:0 8:00 SRC=60.12.192.38 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=45 ID=0 DF PROTO=UDP SPT=46058 DPT=1026 LEN=467
[17179860.132000] EXT3-fs: Unrecognized mount option "nls=utf8" or missing value
[17179884.960000] EXT3-fs: Unrecognized mount option "nls=utf8" or missing value
```

more /etc/fstab reveals:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/hda5     ext3    defaults,nls=utf8,umask=007,gid=46 0
   1
/dev/hda1       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```
sudo mount /dev/hda5 still says:

```
mount: wrong fs type, bad option, bad superblock on /dev/hda5,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by kebes on 2007-01-15
Edit fstab again ("sudo nano /etc/fstab") and change the mount options for your drive. You see where it says "defaults,nls=utf8,umask=007,gid=46" ... looks to me like it's still using the old NTFS options... try switching that to just "defaults" and nothing else. Then see if it now mounts (reboot or "sudo mount -a").

If it still doesn't work, post "dmesg | tail" again... I think we are getting closer.

---

### Post by zerosystem on 2007-01-15
There is definite progress!

After I edited the file in nano just like you said in your last post, the drive is now mounted, but I can't do anything to it other than read, I can't change the permissions, and I can't unmount it either. It's now called 79.0 GB Volume: hda5, mounted on /media/hda5 and there is one folder in it, called "lost+found".

more /etc/fstabL:

 ```
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/hda5     ext3    defaults        0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

dmesg | tail:

```
[17181813.208000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=60.190.218.101 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=53 ID=0 DF PROTO=UDP SPT=52315 DPT=1027 LEN=467
[17181833.620000] kjournald starting.  Commit interval 5 seconds
[17181833.620000] EXT3 FS on hda5, internal journal
[17181833.620000] EXT3-fs: mounted filesystem with ordered data mode.
[17181879.220000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=88.191.35.64 DST=154.20.180.149 LEN=428 TOS=0x00 PREC=0x00 TTL=50 ID=0 DF PROTO=UDP SPT=45364 DPT=1026 LEN=408
[17181929.880000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=207.24.4.236 DST=154.20.180.149 LEN=908 TOS=0x00 PREC=0x00 TTL=118 ID=58071 PROTO=UDP SPT=9759 DPT=1026 LEN=888
[17181941.636000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=221.12.113.254 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=54319 DPT=1027 LEN=467
[17181954.500000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=221.12.113.246 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=49729 DPT=1026 LEN=467
[17181954.504000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=221.12.113.246 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=49731 DPT=1027 LEN=467
[17181960.300000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=118.199.178.110 DST=154.20.180.149 LEN=404 TOS=0x00 PREC=0x00 TTL=52 ID=53416 PROTO=UDP SPT=30822 DPT=1026 LEN=384
```

---

### Post by kebes on 2007-01-15
You just need to change "defaults" to something that gives normal users permission to change it also... I think it's something like


auto,users,rw,exec,uid=bob,gid=bob

(replace "bob" with your username)... First try just changing it from "defaults" to "defaults,users,rw" and see if that fixes it.... it not add/change options as needed.

Hope it works...

---

### Post by zerosystem on 2007-01-15
It's different now, the drive isn't in the computer folder (from the places menu), it's in /media/, named hda5.

The permissions have changed, owner, group, and other can read and execute, only owner can write, and apparently I am not owner. I tried each and every option, but I still cannot write. As of right now, the line for /dev/hda5 reads 
```

auto,users,rw,exec,uid=*,gid=*
```

sudo mount -a

```
[mntent]: line 1 in /etc/fstab is bad
```

dmesg | tail

```
[17183047.004000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=61.138.137.10 DST=154.20.180.149 LEN=926 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=41251 DPT=1027 LEN=906
[17183188.844000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=221.12.113.254 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=33814 DPT=1027 LEN=467
[17183372.884000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=221.6.163.50 DST=154.20.180.149 LEN=485 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=57952 DPT=1026 LEN=465
[17183372.888000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=221.6.163.50 DST=154.20.180.149 LEN=485 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=57952 DPT=1027 LEN=465
[17183372.892000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=221.6.163.50 DST=154.20.180.149 LEN=485 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=57952 DPT=1027 LEN=465
[17183560.724000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=60.12.194.5 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=47 ID=0 DF PROTO=UDP SPT=36840 DPT=1027 LEN=467
[17183630.984000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=60.12.192.38 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=45 ID=0 DF PROTO=UDP SPT=46053 DPT=1026 LEN=467
[17184179.988000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=60.11.125.55 DST=154.20.180.149 LEN=485 TOS=0x00 PREC=0x00 TTL=45 ID=0 DF PROTO=UDP SPT=32983 DPT=1027 LEN=465
[17184332.732000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=24.109.123.16 DST=154.20.180.149 LEN=674 TOS=0x00 PREC=0x00 TTL=118 ID=30107 PROTO=UDP SPT=19089 DPT=1026 LEN=654
[17184347.592000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=204.16.209.20 DST=154.20.180.149 LEN=478 TOS=0x00 PREC=0x00 TTL=55 ID=0 DF PROTO=UDP SPT=43979 DPT=1026 LEN=458
```

more /etc/fstabL

 ```
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/hda5     ext3    defaults,auto,users,rw,exec,uid=stargazer,gid=stargazer        0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Edit: Aha, I've got it working, but it's a slight pain to have to access it from /media/ every time. I typed in 

```
gksudo nautilus
```

navigated to where the partition was, and then edited the permissions and user/user group.

Now, all I want to do is figure out what it means by the

```
sudo mount -a
[mntent]: line 1 in /etc/fstab is bad
```

and get it back to when the partition appeared as another dirve, not a folder located in some obscure place.

---

### Post by kebes on 2007-01-15
Did you try replacing "defaults" with "auto,users,rw,exec,uid=bob,gid=bob" (instead of having both of them there...)...?

---

### Post by zerosystem on 2007-01-16
I've already changed it, it now states:
```

defaults,user
```

I already said earlier that I ran Nautilus as root, and so now I can read, write, and execute from the partition.

This seems like a solution to my problem, but can anyone explain what he did exactly?

Thanks for all the help, kebes! It seems to be working now. I'm not sure what it did last time, but it's fine now, I can read and write and mount the drive now! Just for the record, I'll post up what is shown in the terminal anyway for reference.

more /etc/fstab

 ```
/etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /media/hda5     ext3    defaults,user        0       1
/dev/hda1       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

dmesg | tail

```
[17179756.676000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=60.11.125.46 DST=154.20.180.149 LEN=928 TOS=0x00 PREC=0x00 TTL=45 ID=0 DF PROTO=UDP SPT=55891 DPT=1027 LEN=908
[17179787.136000] agpgart: Found an AGP 2.0 compliant device at 0000:00:00.0.
[17179787.136000] agpgart: Putting AGP V2 device at 0000:00:00.0 into 4x mode
[17179787.136000] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[17179976.684000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=215.138.148.88 DST=154.20.180.149 LEN=512 TOS=0x00 PREC=0x00 TTL=51 ID=57566 PROTO=UDP SPT=30822 DPT=1026 LEN=492
[17179978.676000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=87.249.104.224 DST=154.20.180.149 LEN=60 TOS=0x00 PREC=0x00 TTL=44 ID=42060 DF PROTO=TCP SPT=34638 DPT=6891 WINDOW=5840 RES=0x00 SYN URGP=0
[17179981.676000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=87.249.104.224 DST=154.20.180.149 LEN=60 TOS=0x00 PREC=0x00 TTL=44 ID=42061 DF PROTO=TCP SPT=34638 DPT=6891 WINDOW=5840 RES=0x00 SYN URGP=0
[17180012.208000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=24.238.57.14 DST=154.20.180.149 LEN=758 TOS=0x00 PREC=0x00 TTL=118 ID=64413 PROTO=UDP SPT=22281 DPT=1026 LEN=738
[17180187.044000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=221.12.113.254 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=58309 DPT=1026 LEN=467
[17180187.048000] Inbound IN=eth0 OUT= MAC=00:40:ca:3c:6c:68:00:90:1a:40:f2:1e:08:00 SRC=221.12.113.254 DST=154.20.180.149 LEN=487 TOS=0x00 PREC=0x00 TTL=46 ID=0 DF PROTO=UDP SPT=58311 DPT=1027 LEN=467

```

Also, a little note, it seems that when Ubuntu notices that 100% of the hard drive space is taken, it won't let you log in as any user, you have to log in as "root" when you boot up and with the root password, and you have to make some space on the drive/partition.

---

