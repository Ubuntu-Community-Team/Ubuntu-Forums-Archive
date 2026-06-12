---
title: "Media file/drive access problems"
date: 2009-01-30
forum: General Help
---

### Post by mikemac on 2009-01-30
I am having consistent problems with mounting/using USB storage devices.  I have tried thumb drives, an external CD-ROM, a 160GB external drive, and the Seagate drive shown in the following text:

 dmesg |tail -n20
[ 9101.940062] usb 6-9: new high speed USB device using ehci_hcd and address 4
[ 9102.089870] usb 6-9: configuration #1 chosen from 1 choice
[ 9102.105395] scsi7 : SCSI emulation for USB Mass Storage devices
[ 9102.110249] usb-storage: device found at 4
[ 9102.110264] usb-storage: waiting for device to settle before scanning
[ 9107.109723] usb-storage: device scan complete
[ 9107.111966] scsi 7:0:0:0: Direct-Access     Seagate  FreeAgentDesktop 100D PQ: 0 ANSI: 4
[ 9107.117168] sd 7:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 9107.119288] sd 7:0:0:0: [sdb] Write Protect is off
[ 9107.119300] sd 7:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[ 9107.119307] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 9107.122538] sd 7:0:0:0: [sdb] 488397168 512-byte hardware sectors (250059 MB)
[ 9107.126809] sd 7:0:0:0: [sdb] Write Protect is off
[ 9107.126824] sd 7:0:0:0: [sdb] Mode Sense: 1c 00 00 00
[ 9107.126831] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 9107.128087]  sdb: sdb1
[ 9107.165973] sd 7:0:0:0: [sdb] Attached SCSI disk
[ 9107.167938] sd 7:0:0:0: Attached scsi generic sg2 type 0
[ 9369.919154] sd 7:0:0:0: [sdb] Result: hostbyte=DID_OK driverbyte=DRIVER_OK,SUGGEST_OK
[ 9369.919178] end_request: I/O error, dev sdb, sector 119369

I am having problems accessing this drive (and all others, except for my physical hard drive).  I have tried chmod and chown to no avail.  The following is the error I get:
 cd media
bash: cd: media: Permission denied

I can only access the media folder when actually logged in as root.  I have looked throughout these forums, and Googled extensively and found older problems that sound like they relate; but no definite fix for them.

I am running Ubuntu 8.10 as a dual-boot with WinXP (which is only there due to inertia...)

Thanks for any help!

---

### Post by taurus on 2009-01-30
What filesystem is your Seagate FreeAgentDesktop USB drive?

Make sure the drive is still plugged in.  Then, open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by Yellow Pasque on 2009-01-30
One solution I have seen to USB permission errors is adding your user to the plugdev group if it isn't already.
```
sudo adduser <YOUR_USER_NAME> plugdev 
```

---

### Post by mikemac on 2009-01-30
> **taurus said:**
> What filesystem is your Seagate FreeAgentDesktop USB drive?

Make sure the drive is still plugged in.  Then, open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

```
sudo fdisk -l
[sudo] password for mikemac: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2505    20121381    7  HPFS/NTFS
/dev/sda2            2506       19457   136166940    5  Extended
/dev/sda5            2506       19231   134351563+  83  Linux
/dev/sda6           19232       19457     1815313+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47dd1ef8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244198552+   b  W95 FAT32

 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             127G  5.3G  115G   5% /
tmpfs                 948M     0  948M   0% /lib/init/rw
varrun                948M  216K  948M   1% /var/run
varlock               948M     0  948M   0% /var/lock
udev                  948M  2.8M  946M   1% /dev
tmpfs                 948M  164K  948M   1% /dev/shm
lrm                   948M  2.0M  946M   1% /lib/modules/2.6.27-11-generic/volatile
df: `/media/MEDIA_DRIVE': Permission denied


```

---

### Post by mikemac on 2009-01-30
> **Temüjin said:**
> One solution I have seen to USB permission errors is adding your user to the plugdev group if it isn't already.
```
sudo adduser <YOUR_USER_NAME> plugdev 
```

Already a member :(

---

### Post by mikemac on 2009-01-30
Tried the information found on this thread:
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/221983") and that didn't work, either.

---

### Post by taurus on 2009-01-30
What happens if you try to mount your drive, /dev/sdb1, as

```
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

---

### Post by mikemac on 2009-01-30
> **taurus said:**
> What happens if you try to mount your drive, /dev/sdb1, as

```
sudo umount /dev/sdb1
sudo mkdir /media/sdb1
sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
df -h
```

Here it is:
```
mikemac@mikemac-laptop:~$ sudo umount /dev/sdb1
[sudo] password for mikemac: 
mikemac@mikemac-laptop:~$ sudo mkdir /media/sdb1
mikemac@mikemac-laptop:~$ sudo mount -t vfat /dev/sdb1 /media/sdb1 -o umask=000
mikemac@mikemac-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             127G  5.3G  115G   5% /
tmpfs                 948M     0  948M   0% /lib/init/rw
varrun                948M  216K  948M   1% /var/run
varlock               948M     0  948M   0% /var/lock
udev                  948M  2.8M  946M   1% /dev
tmpfs                 948M  164K  948M   1% /dev/shm
lrm                   948M  2.0M  946M   1% /lib/modules/2.6.27-11-generic/volatile
df: `/media/sdb1': Permission denied

```

---

### Post by taurus on 2009-01-30
Looks like you have windows on your machine, /dev/sda1, so maybe you want to boot it up.  Then, run a scandisk and defrag of that external drive.  Once it's done, reboot to Ubuntu and see if you can mount/access it now.

---

### Post by mikemac on 2009-01-30
I'll try that and post back.  Thanks for the advice!

---

### Post by mikemac on 2009-01-30
Defragged the drive, still can't access.  Never mentioned before, but the error I get from Gnome when I try opening the drive is attached.  But the error message states: Could not display "Media/Media_Drive". There is no application for this file.

Any more advice?

---

### Post by taurus on 2009-01-30
Can you post the outputs of these two commands again?

```
sudo fdisk -l
df -h
```

---

### Post by mikemac on 2009-01-31
Here it is:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2505    20121381    7  HPFS/NTFS
/dev/sda2            2506       19457   136166940    5  Extended
/dev/sda5            2506       19231   134351563+  83  Linux
/dev/sda6           19232       19457     1815313+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x47dd1ef8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30402   244198552+   b  W95 FAT32
mikemac@mikemac-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             127G  5.3G  115G   5% /
tmpfs                 948M     0  948M   0% /lib/init/rw
varrun                948M  212K  948M   1% /var/run
varlock               948M     0  948M   0% /var/lock
udev                  948M  2.8M  946M   1% /dev
tmpfs                 948M  156K  948M   1% /dev/shm
lrm                   948M  2.0M  946M   1% /lib/modules/2.6.27-11-generic/volatile
df: `/media/MEDIA_DRIVE': Permission denied

```

I have also found that I have full access to the external drive (able to view directories, subdirectories, and files) when logged in as SU (but I don't really want to operate as SU all the time.  While in each directory, I again tried to chmod (recursively), but it has not changed my permissions (apparently).

---

### Post by taurus on 2009-01-31
What about the output of this command?

```
sudo ls -la /media
```
Do you have anything important on that drive?  Maybe you just want to reformat it.

---

### Post by mikemac on 2009-01-31
```
total 84
d--------- 13 mikemac root     4096 2009-01-30 21:50 .
drwxr-xr-x 20 root    root     4096 2009-01-28 22:24 ..
lrwxrwxrwx  1 root    root        6 2009-01-27 09:47 cdrom -> cdrom0
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-27 09:47 cdrom0
-rw-r--r--  1 root    root      117 2009-01-30 21:50 .hal-mtab
-rw-------  1 root    root        0 2009-01-30 21:50 .hal-mtab-lock
drwx------ 10 mikemac root    32768 1969-12-31 18:00 MEDIA_DRIVE
drwxrwxrwx  2 root    root     4096 2009-01-30 16:53 sdb1
lrwxrwxrwx  1 root    root        4 2009-01-30 10:26 usb -> usb0
drwxrwxrwx  2 root    root     4096 2009-01-30 10:26 usb0
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-30 10:26 usb1
drwxrwxrwx  2 root    root     4096 2009-01-30 10:26 usb2
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-30 10:26 usb3
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-30 10:26 usb4
drwxrwxrwx  2 root    root     4096 2009-01-30 10:26 usb5
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-30 10:26 usb6
drwxrwxrwx  2 root    root     4096 2009-01-30 10:26 usb7

```

---

### Post by mikemac on 2009-01-31
> **taurus said:**
> 
Do you have anything important on that drive?  Maybe you just want to reformat it.

I'd reformat; but:
                   #1  It would be a huge hassle
                   #2  I reformatted one of my USB thumbdrives multiple     
                       times, and it didn't help
                   #3  Since this is happening with multiple devices, I'm 
                       hoping that the fix for one will work for all.

---

### Post by taurus on 2009-01-31
> **mikemac said:**
> ```
total 84
**[COLOR="Red"]d--------- 13 mikemac root     4096 2009-01-30 21:50 .[/COLOR]**
drwxr-xr-x 20 root    root     4096 2009-01-28 22:24 ..
lrwxrwxrwx  1 root    root        6 2009-01-27 09:47 cdrom -> cdrom0
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-27 09:47 cdrom0
-rw-r--r--  1 root    root      117 2009-01-30 21:50 .hal-mtab
-rw-------  1 root    root        0 2009-01-30 21:50 .hal-mtab-lock
drwx------ 10 mikemac root    32768 1969-12-31 18:00 MEDIA_DRIVE
drwxrwxrwx  2 root    root     4096 2009-01-30 16:53 sdb1
lrwxrwxrwx  1 root    root        4 2009-01-30 10:26 usb -> usb0
drwxrwxrwx  2 root    root     4096 2009-01-30 10:26 usb0
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-30 10:26 usb1
drwxrwxrwx  2 root    root     4096 2009-01-30 10:26 usb2
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-30 10:26 usb3
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-30 10:26 usb4
drwxrwxrwx  2 root    root     4096 2009-01-30 10:26 usb5
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-30 10:26 usb6
drwxrwxrwx  2 root    root     4096 2009-01-30 10:26 usb7

```

Try these.

```
sudo chmod 755 /media
ls -la /media
```

---

### Post by mikemac on 2009-01-31
Thank you - that definitely did it:
 
```
 ls -la /media
total 84
drwxr-xr-x 13 mikemac root     4096 2009-01-30 21:50 .
drwxr-xr-x 20 root    root     4096 2009-01-28 22:24 ..
lrwxrwxrwx  1 root    root        6 2009-01-27 09:47 cdrom -> cdrom0
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-27 09:47 cdrom0
-rw-r--r--  1 root    root      117 2009-01-30 21:50 .hal-mtab
-rw-------  1 root    root        0 2009-01-30 21:50 .hal-mtab-lock
drwx------ 10 mikemac root    32768 1969-12-31 18:00 MEDIA_DRIVE
drwxrwxrwx  2 root    root     4096 2009-01-30 16:53 sdb1
lrwxrwxrwx  1 root    root        4 2009-01-30 10:26 usb -> usb0
drwxrwxrwx  2 root    root     4096 2009-01-30 10:26 usb0
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-30 10:26 usb1
drwxrwxrwx  2 root    root     4096 2009-01-30 10:26 usb2
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-30 10:26 usb3
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-30 10:26 usb4
drwxrwxrwx  2 root    root     4096 2009-01-30 10:26 usb5
drwxrwxrwx  2 mikemac mikemac  4096 2009-01-30 10:26 usb6
drwxrwxrwx  2 root    root     4096 2009-01-30 10:26 usb7

```

I can probably now recreate this for my other external drive/thumbdrive (I'm guessing)

---

### Post by taurus on 2009-01-31
You should be able to access all your external drives now when you plug them in.

```
df -h
ls -la /media/MEDIA_DRIVE
```

---

### Post by Ziggy72 on 2009-01-31
This problem may have already been solved... I'm a bit confused.

However, if not, let us suppose you want to mount files on /dev/sda5 at every boot.

```

sudo cd /media
mkdir sda5 

```

add a line to /etc/fstab:
> 
# /dev/sda5
/dev/sda5	/media/sda5	ext3    defaults	 0       1


Check that this works with
```
sudo mount -a
```

If that doesn't work, it may be that the word "defaults" should be replaced with "relatime,errors=remount-ro" and/or if your filesystem is ext2, replace ext3 with ext2.

If mounting works, the drive or partition will be visible on your desktop at each reboot.

Give this a try - nothing to lose. If it works ok you'll be able to extend this to access any other disks or partitions you want to explore. For each disk or partition you want to mount and enter in fstab, you'll need to have an appropriate mount point entry in /media.

I'm no expert, but I hope this helps...

---

### Post by mikemac on 2009-01-31
I'll keep this in mind - thanks for the advice.  But in this case, I don't want the device mounted with every boot.  The drive is media that I'm swapping between inside the house and my CarPC.  No sense in having the computer try to mount a drive that's outside in my car...

---

