---
title: "Could not able to run the executable from the USB flash drive only in Ubuntu 10.10"
date: 2010-10-20
forum: Desktop Environments
---

### Post by webrsk on 2010-10-20
All the steps tried under root login.
I was trying to run a executable file from a USB flash drive on ubuntu 10.10. Its works fine if i run the file from the hard drive or the same USB drive executable works fine in Ubuntu 10.04. The file is already set to 777 permission but when opening in ubuntu 10.10 it only shows read+write permission. Chmod 777 not works though.

For testing :
I created a file in the hard disk ( / ) and set the (chmod +x -R) permission which is applied but after i copied the file to the USB drive the permission automatically changes to -rw-r--r--  instead of -rwxr-xr-x .

I searched release notes of 10.10 but it doesn't have information about this. Not sure this is a bug or security restrictions!!

---

### Post by jbarcelo on 2010-10-20
I'm facing a similar problem :)

I cannot change the permissions of the files in my USB drive.

root@antartida:/media/USB20FD/uc3m/sync_scripts# ls -l
total 32
-rw-r--r-- 1 jbarcelo jbarcelo 132 2010-02-02 09:15 backup_to_laptop
-rw-r--r-- 1 jbarcelo jbarcelo 145 2010-01-30 09:30 backup_to_luciernaga
root@antartida:/media/USB20FD/uc3m/sync_scripts# chmod 777 *
root@antartida:/media/USB20FD/uc3m/sync_scripts# ls -l
total 32
-rw-r--r-- 1 jbarcelo jbarcelo 132 2010-02-02 09:15 backup_to_laptop
-rw-r--r-- 1 jbarcelo jbarcelo 145 2010-01-30 09:30 backup_to_luciernaga
root@antartida:/media/USB20FD/uc3m/sync_scripts#

---

### Post by utilitytrack on 2010-10-20
> **webrsk said:**
> Not sure this is a bug or security restrictions!!

Not enough info for conclusions. But here is described similar case: [http://ubuntuforums.org/showthread.php?t=1600759]("http://ubuntuforums.org/showthread.php?t=1600759")

Anyway try this:
```
# mount -o remount,exec,rw,dev,async <usb_device> <mountpoint>

```

---

### Post by jbarcelo on 2010-10-20
Thanks for the suggestion utilitytrack.

I tried the command you proposed, but apparently it makes no difference:

root@antartida:/media/USB20FD/uc3m/sync_scripts# mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jbarcelo/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jbarcelo)
/dev/sdb1 on /media/USB20FD type vfat (rw)
root@antartida:/media/USB20FD/uc3m/sync_scripts# mount -o remount,exec,rw,dev,async /dev/sdb1 /media/USB20FD/
root@antartida:/media/USB20FD/uc3m/sync_scripts# chmod 777 *
root@antartida:/media/USB20FD/uc3m/sync_scripts# ls -l
total 32
-rw-r--r-- 1 jbarcelo jbarcelo 132 2010-02-02 09:15 backup_to_laptop
-rw-r--r-- 1 jbarcelo jbarcelo 145 2010-01-30 09:30 backup_to_luciernaga
root@antartida:/media/USB20FD/uc3m/sync_scripts#

---

### Post by webrsk on 2010-10-21
Guess ubuntu 10.10 auto mounting not allows to change the file/folder permissions or execute the file from the usb drive . 

It can be fixed manually by mounting the usb drive as mentioned below.

#1
Create a folder in /media to mount the usb data:   > mkdir usb

#2
Identify the USB device which is connected : > fdisk -l
Which shows the usb device like:   /dev/sdc1

#3
Now add an entry in /etc/fstab   : 
/dev/sdc1 /media/usb vfat umask=0222,auto,users,exec 0 0

#4
Save and quit.

#5
> mount /media/usb

Check your files in /media/usb which has executable permission and you can change the permission as wish.

> unmount /media/usb


Still waiting to know the right answer , is it ubuntu 10.10 release doesnt mount USB drive with executable permission due to security restriction or is it a bug !!!

---

### Post by jbarcelo on 2010-10-21
Thanks webrsk. Your solution works for me.

---

### Post by kcpoole on 2010-12-27
What has changed in 10.10?

I have the same problem on and external hard disk I use for backup.

Previously I used Ubuntu 9.04, and my shell script on the External drive worked fine.
After installing U10.10, U can no longer execute the shell scripts on the drive, nor change the permissions on them
I amd the owner of the files on the drive and can create new files, and delete existing ones but no execute!

I do not mount the drive at permanently as it is my offsite storage so manually creating a mount in fstab is no good

Any way to revert to ?

Yet another thing thats broken it 10.10

ken

---

### Post by sid32 on 2011-01-19
The problem is with the Udisk package. Downgrade to 1.0.1build1 and then pin it in synaptic.

---

### Post by sid32 on 2011-01-19
The problem is with the Udisk package. Downgrade to 1.0.1build1 and then pin it in synaptic.

---

### Post by sid32 on 2011-01-19
I had this happen to me in 10.10. The issue seems to be with the newest udisk. 

To fix open synaptic (system - admin -synaptic). Check your udisk version number. See if there is a newer version...

---

