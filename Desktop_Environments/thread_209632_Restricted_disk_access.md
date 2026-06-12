---
title: "Restricted disk access"
date: 2006-07-05
forum: Desktop Environments
---

### Post by turingbombe on 2006-07-05
I just installed ubuntu recently and I am having some problems setting up a hard drive. I have 2 in my computer, 1 is only used for multimedia. I formatted the drive I now am using to run ubuntu, but the multimedia drive is not accessible. When I'm in "File Browser" looking at my computer it shows up as "111.8 GB Volume : /tmp/disks-conf-sdb1"  When I try to open it it says contents can't be displayed and that I don't have 'permissions' to access the contents, which I should. It says that the file owner and file group are both "root". I don't know how to change this. Any suggestions on how to get access without formatting?

After trying to change the permissions in the terminal it says this:
chmod: changing permissions of `disks-conf-sdb1': Read-only file system

---

### Post by tonyr on 2006-07-05
Provide somemore information, please.  What kind of drive is the multimedia drive? Is
it internal or external?  How was it formatted: Linux? Windows Fat32? Windows NTFS?

Open a terminal (**Applications->Accessories->Terminal**), type this
```

sudo fdisk -l
mount
cat /etc/fstab

```
and post the output here.  (That's ELL, not EYE, in the **fdisk** line).

---

### Post by zhoux on 2006-07-05
is your multimedia system formatted as NTFS? because currently, linux doesn't support ntfs writing...only reading....thus "Read-Only"

---

### Post by turingbombe on 2006-07-05
The drive is an NTFS formatted disk and it is an internal hard drive

After : fdisk -L
Disk /dev/sda: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14589     4771305    5  Extended
/dev/sda5           13996       14589     4771273+  82  Linux swap / Solaris

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14589   117186111    7  HPFS/NTFS


After 'mount'
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-25-386/volatile type tmpfs (rw)
/dev/sdb1 on /tmp/disks-conf-sdb1 type ntfs (rw)

After cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb /media/windows ntfs umask=0222 0 0

NOTE: I changed the mount point on sdb after reading a few things about this, it didnt' seem to do anything.

---

### Post by aysiu on 2006-07-05
http:;//www.psychocats.net/ubuntu/mountwindows should help.

---

### Post by turingbombe on 2006-07-05
after following the tutorial from aysiu , which is similar to what i did before i get this message after the "sudo mount -a" cmd:
mount: /dev/sdb1 already mounted or /media/windows busy
mount: according to mtab, /dev/sdb1 is mounted on /tmp/disks-conf-sdb1

---

### Post by tonyr on 2006-07-05
..I don't remember everything that's in the article at **aysiu**'s link, but I'll bet
it shows more than just **umask** for the mount options in the **fstab** file
(**/etc/fstab**) .  At least try
```

dev/sdb /media/windows ntfs **defaults**,umask=0222 0 0

```

---

### Post by aysiu on 2006-07-05
It looks from your /etc/fstab that you are trying to mount /dev/sdb instead of /dev/sdb1.

It also looks as if it's already mounted at /tmp/disks-conf-sdb1 instead of /media/windows (where you're trying to mount it).

```
sudo umount /dev/sdb1
sudo mkdir /media/windows
sudo nano /etc/fstab
``` Change this line ```
/dev/sdb /media/windows ntfs umask=0222 0 0
``` to this ```
/dev/sdb1 /media/windows ntfs nls=utf8,umask=0222 0 0
``` Save and then ```
sudo mount -a
``` If you get an error with the second command saying that the folder already exists, that's okay--just go to the next step.

---

### Post by tonyr on 2006-07-05
[QUOTE=turingbombe]after following the tutorial from aysiu , which is similar to what i did before i get this message after the "sudo mount -a" cmd:
mount: /dev/sdb1 already mounted or /media/windows busy
mount: according to mtab, /dev/sdb1 is mounted on /tmp/disks-conf-sdb1[/QUOTE]

Did you
```

sudo umount /dev/sdb1

```
before you did the **mount -a**?  And in order to do the **umount** successfully,
there should be no applications (terminals etc) using that partition.

---

### Post by turingbombe on 2006-07-05
when i do that i just get this response.
mount: /dev/sdb already mounted or /media/music busy

when i change /dev/sdb to /dev/sdb1 then it just ads the message that it is already mounted at /tmp/disks-conf-sdb1

---

### Post by aysiu on 2006-07-05
[QUOTE=turingbombe]when i do that i just get this response.
mount: /dev/sdb already mounted or /media/music busy

when i change /dev/sdb to /dev/sdb1 then it just ads the message that it is already mounted at /tmp/disks-conf-sdb1[/QUOTE]
Follow the steps I outlined exactly in the order I outlined them.

To sum up, they do this:

1. Unmount /dev/sdb1

2. Make a directory called /media/windows (if it already exists, that's okay--we just want to make sure it's there.

3. Edit the /etc/fstab to tell it to use /media/windows instead of that other weird mount point.

4. Remount /dev/sdb1 to the new mount point.

---

### Post by turingbombe on 2006-07-05
Did not do the umount, just did that and now everything is working properly, thanks a lot! Someone said that I can't write to NTFS? So this drive will have to be read only unless I format it and make it linux?

---

### Post by aysiu on 2006-07-05
[QUOTE=turingbombe]Did not do the umount, just did that and now everything is working properly, thanks a lot! Someone said that I can't write to NTFS? So this drive will have to be read only unless I format it and make it linux?[/QUOTE]
NTFS is read-only for Linux.

FAT32 is read/write for both Linux *and* Windows.

Ext3 is read/write for Linux, of course, but it can be read/write for Windows also if you install this driver: [http://www.fs-driver.org](http://www.fs-driver.org)

---

### Post by tonyr on 2006-07-05
High Five all around.

---

