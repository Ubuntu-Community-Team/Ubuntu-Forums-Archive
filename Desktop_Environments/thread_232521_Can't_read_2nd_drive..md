---
title: "Can't read 2nd drive."
date: 2006-08-08
forum: Desktop Environments
---

### Post by shawnanigans on 2006-08-08
I can't seem to get Ubuntu to read my 2nd drive. I just installed and it can be read when I boot into Windows. I have both Windows and Linux on a 120 gb drive in 20gb partitions. Thanks in advance for the help.

---

### Post by hopstah on 2006-08-08
> **shawnanigans said:**
> I can't seem to get Ubuntu to read my 2nd drive. I just installed and it can be read when I boot into Windows. I have both Windows and Linux on a 120 gb drive in 20gb partitions. Thanks in advance for the help.
is the drive mounted?  post the contents of your /etc/fstab file here so we can see what's being mounted at boot.

---

### Post by shawnanigans on 2006-08-08
No it isn't mounted it will not mount that would be the problem, right now seems like an important thing to not put up but ya it is not mountable apparently says; error: device /dev/sdb1 is not removable

error: could not execute pmount

Also /etc/fstab doesnt seem to exist.

---

### Post by hopstah on 2006-08-08
when you type in ```
sudo gedit /etc/fstab
``` what shows up?

you have to have an fstab file somewhere.

---

### Post by shawnanigans on 2006-08-08
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda7       /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

I think you can tell I'm new to linux.

---

### Post by hopstah on 2006-08-08
ok, i'll explain a little bit about this file for you.

/dev/sda5 is being mounted at your root (/) and it has the filesystem of ext3.  this is the partition that ubuntu is installed on.

/dev/sda1 and /dev/sda7 are two ntfs partitions mounted at /media/sda1 and /media/sda7  are both of these showing up as they should?

below that is the mount information for your swap and cdrom.

when you say your 2nd drive isn't showing up, are you talking about a physical second drive in your computer that you want to set up?  if so, it's easy to do, but i just need to know what you're working with here.

---

### Post by shawnanigans on 2006-08-08
First drive is in 4 partitions, 20gb ntfs, 20gb ext3, 2gb swap, 70gb storage. 
Second drive is a 250gb drive formated ntfs and it wont mount.

---

### Post by hopstah on 2006-08-08
try typing this in at a terminal and see what it says ```
sudo mkdir /media/sdb1
sudo mount -t ntfs /dev/sdb1 /media/sdb1
```
and report back the results.

---

### Post by shawnanigans on 2006-08-08
Did it and now it says I don't have permission to mount the drive.

---

### Post by shawnanigans on 2006-08-08
You do not have the permissions necessary to view the contents of "sdb1". Is the exact message.

---

### Post by hopstah on 2006-08-08
are you doing this from a user who has administration priveledges?

try adding this line to the bottom of your /etc/fstab file```
/dev/sdb1 /media/sdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
```

---

### Post by shawnanigans on 2006-08-08
I'm doing this from the only account I have so it should have administrative privilages. However I can't make changes to fstab because its read only and I cant change that either because I am not the owner, whatever that means. I'm not the owner of anything in root.

---

### Post by hopstah on 2006-08-08
you don't need to be the owner as long as you preface any commands where you need to be root with 'sudo'

for example, type ```
sudo gedit /etc/fstab
``` and you will open gedit with root priviledges and you will be able to edit the file.  once you can do that, add that line to the bottom of it, save the file, and then reboot your computer.  with that done, your drive should be automagically mounted when you boot up.  give that a go and get back to me.

---

### Post by shawnanigans on 2006-08-09
You have done it my good man. Thanks, I can now get to my drive.

---

### Post by hopstah on 2006-08-09
my pleasure. :)

---

### Post by kurup on 2006-08-09
Hi..have been trying to figure this problem with my boot-up for a couple of days now. The grub fails to boot into windows which is my first partition. My fstab looks like this.
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


and this is how my fdisk /dev/hda looks like:
> 
Disk /dev/hda: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/hda2            1306        4780    27912937+  83  Linux
/dev/hda3            4781        4870      722925    5  Extended
/dev/hda5            4781        4870      722893+  82  Linux swap / Solaris


Any idea what could be happening?

Thanks in advance.

---

### Post by GoLoGo on 2006-08-09
you need to edit your menu.lst so you can choose windows xp.

```
sudo gedit /boot/grub/menu.lst

title           Windows XP Professional SP2
rootnoverify    (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

That should work, unless you have some strange setup.

---

