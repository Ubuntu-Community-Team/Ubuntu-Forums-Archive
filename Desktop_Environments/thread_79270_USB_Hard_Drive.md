---
title: "USB Hard Drive"
date: 2005-10-19
forum: Desktop Environments
---

### Post by irv on 2005-10-19
This is not totally relaited to Ubuntu 5.1, just before I upgraded from 5.04 I found that I could not write to my 250MB USB Hard Drive. I have read and Exicute rights only. And the system will not let me change the atribuits for myself. I though that after the upgrade this might fix the problem but it didn't.
The message I get when trying to change the atribuits is:
The permissions could not be changed. 
Couldn't change the permissions of "USB Drive" because it is on a read-only disk.

This is not true. It must think it is a CD or something like that.
Anyone have an idea how to fix this problem?:confused:

---

### Post by dbott67 on 2005-10-19
Right-click your USB drive & select properties.  Select the PERMISSIONS tab.  Who is listed as the owner of the device & what permissions do you see?

If your current user account is not the owner, you will need to run 'chown' to change the ownership to your account.  If the USB drive auto-mounts to your desktop:

1. Open a terminal and type:
```
cd ~/Desktop
```
2. Next, type in the following command, replacing ***dbott*** with your own user account, and ***usb_device_name*** with the name of your USB drive as it appears on the desktop:
```
dbott@breezy:~/Desktop$ sudo chown dbott:dbott usb_device_name
```

Type 'man chown' for full usage.

-Dave

---

### Post by migueljacq on 2005-10-19
[QUOTE=irv]This is not totally relaited to Ubuntu 5.1, just before I upgraded from 5.04 I found that I could not write to my 250MB USB Hard Drive. I have read and Exicute rights only. And the system will not let me change the atribuits for myself. I though that after the upgrade this might fix the problem but it didn't.
The message I get when trying to change the atribuits is:
The permissions could not be changed. 
Couldn't change the permissions of "USB Drive" because it is on a read-only disk.

This is not true. It must think it is a CD or something like that.
Anyone have an idea how to fix this problem?:confused:[/QUOTE]

I'm thinking edit your /etc/fstab file. The drive will probably be listed as a line in there since it's mounting. The problem is there is probably an 'ro' mentioned under the 'options' section. I'm wondering if changing it to 'rw' will help. If not, you can always change it back and wait for someone with more knowledge than me to respond :)

EDIT: Ahh, I see someone already did :)

---

### Post by irv on 2005-10-19
This worked to change owner, but it still won't let me write to the drive.
I did:  (  chown irv:irv USB_Drive   ) and this changed the owner from root to irv, but if I try to change the atribuites to write, I get the same message the it is a read only.
I feel like I am in a hole that keep getting deeper. :confused:  still confused!

---

### Post by migueljacq on 2005-10-19
[QUOTE=irv]This worked to change owner, but it still won't let me write to the drive.
I did:  (  chown irv:irv USB_Drive   ) and this changed the owner from root to irv, but if I try to change the atribuites to write, I get the same message the it is a read only.
I feel like I am in a hole that keep getting deeper. :confused:  still confused![/QUOTE]

Have a look at this thread and let us know if it helps:

[http://ubuntuforums.org/showthread.php?t=71679](http://ubuntuforums.org/showthread.php?t=71679)

---

### Post by irv on 2005-10-20
I am back to squard one: I tried chmod and chown and edited fstab file. No matter what I do I can't write to this USB Hard Drive. Even though I am the owner of it now, it seems like it thinks its a CD Disk thats read only.
I also tried [http://ubuntuforums.org/showthread.php?t=71679](http://ubuntuforums.org/showthread.php?t=71679) The thread above.

---

### Post by majikstreet on 2005-10-20
[QUOTE=irv]I am back to squard one: I tried chmod and chown and edited fstab file. No matter what I do I can't write to this USB Hard Drive. Even though I am the owner of it now, it seems like it thinks its a CD Disk thats read only.
I also tried [http://ubuntuforums.org/showthread.php?t=71679](http://ubuntuforums.org/showthread.php?t=71679) The thread above.[/QUOTE]
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

See that page for fstab info.

I can help you along the process.

Could you please tell me the contents of /etc/fstab?

---

### Post by dbott67 on 2005-10-20
Actually, what I'm starting to think is that the hard drive is formatted as NTFS, not FAT32/VFAT.

What is the output of **mount -l**?
```
dbott@breezy:~$ mount -l
/dev/hda3 on / type ext3 (rw,errors=remount-ro) [/]
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hdc on /media/cdrom0 type iso9660 (ro,noexec,nosuid,nodev,user=dbott)
[COLOR="Red"]/dev/sda1 on /media/CORSAIR type vfat (rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)[/COLOR]
```
I have a 512 MB Corsair USB thumb drive.  If you notice the last line in my output, you'll see **/dev/sda1** is mounted as /**media/CORSAIR** and the type is **vfat**.

If yours says NTFS, you won't be able to write to the drive, as NTFS partitions are 'read only'.

You could also try the command:
```
fdisk -l /dev/sda1
```

Note: your USB drive may not be **/dev/sda1**, make note of what it is under the **mount -l**.

-Dave

---

### Post by irv on 2005-10-20
My fstab file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

the dev I am mounting, mount automaticly, it is /dev/sda1.
By the way it is NTFS, this may be why it is read only.
If I try to mount it after it starts it tells me that /media/USB_Drive is already mounted.
Hope this info help?

---

### Post by dbott67 on 2005-10-20
Can you post the output of **mount -l**?

If you take a read of my post just above your last post, you'll see that I have a similar setup to yours.
> the dev I am mounting, mount automaticly, it is** /dev/sda1**.
If I try to mount it after it starts it tells me that **/media/USB_Drive** is already mounted.

So your output of **mount -l** should have a line similar to this:
```
/dev/sda1 on /media/USB_Drive type [COLOR="Red"]vfat[/COLOR] (rw,noexec,nosuid,nodev,quiet,shortname=winnt,uid=1000,gid=1000,umask=077,iocharset=utf8)
```

My USB thumb drive is vfat.  What is your USB Drive?

---

### Post by dbott67 on 2005-10-20
[QUOTE=irv]...By the way it is NTFS, this may be why it is read only.[/QUOTE]

This is exactly why you can't write to it.

2 options for you:

1. Install [captive]("http://www.jankratochvil.net/project/captive/"), which is a new (and early release) of an application that will allow write access to NTFS.

2. Re-partition/re-format your USB Drive to FAT32 (or create multiple partitions; 50% NTFS, 50% FAT32)

-Dave

---

### Post by irv on 2005-10-20
/dev/hda1 on / type ext3 (rw,errors=remount-ro) [/]
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
usbfs on /proc/bus/usb type usbfs (rw)
/dev/hdc on /media/cdrom1 type iso9660 (ro,noexec,nosuid,nodev,user=irv)
/dev/sda1 on /media/USB_Drive type ntfs (rw,noexec,nosuid,nodev,uid=1000,gid=1000,umask=077,iocharset=utf8)

---

### Post by irv on 2005-10-20
Dave 
Thanks for all the help.

---

### Post by dbott67 on 2005-10-20
You're welcome, irv.

Take care,
Dave

---

### Post by majikstreet on 2005-10-21
[QUOTE=irv]Dave 
Thanks for all the help.[/QUOTE]
What did you do to fix it?

---

### Post by irv on 2005-10-21
Nothing yet, but I am going to pull some files off and re-format, so it will work on all platforms, Windows, Linux, Mac, etc. I will just use Fat32.

---

### Post by dbott67 on 2005-10-21
I'm not sure if you're asking what the problem was *(it was that the USB file system was NTFS and that by default, Linux can only read NTFS partitions, not write to them)* or if you're asking what irv did to enable writing to the hard drive. Of course, I'll have to let irv answer that one. EDIT: it looks like irv just answered it! :)

He could also use one of the partition managers (such as **gparted**) to non-destructively resize the NTFS partition to 50% or it's original size and then create a new FAT partition in the newly created free space.

-Dave

---

### Post by irv on 2005-10-22
Just for the record, I re-partitioned the USB 250Gig Hard Drive into three partitions; two Fat32 and one NTSF. This will work for me. My next project will be to network my three computer; two running Linux and one still running WinXP.

---

