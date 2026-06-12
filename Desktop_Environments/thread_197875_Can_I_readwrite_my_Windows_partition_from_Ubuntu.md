---
title: "Can I read/write my Windows partition from Ubuntu?"
date: 2006-06-16
forum: Desktop Environments
---

### Post by dnccnd on 2006-06-16
I have upgraded to Ubuntu 6.06, which is installed in one of my two partitions. On the other partition I have Windows. Both in Breezy and Dapper on my desktop I had/have an icon called "hda1" which is my Windows partition. But when I double-click it a message tells me that I haven't the necessary authorisation to access this hd.

In Breezy I could avoid this problem through Disks Manager by clicking on the browse botton of the partition. Now this trick doesn't work anymore. I get the same message that I get when I try to open the hd from the desktop icon.

Do you know whether there is a way to access the files on my Windows partition and maybe write on it? I know that it isn't that easy to write on Windows partitions, but I thought it could be easier with 6.06.

Thank you...

---

### Post by lazyd2 on 2006-06-16
Please post your /etc/fstab

---

### Post by raptros-v76 on 2006-06-16
sudo apt-get install ntfsprogs

that should allow you to read from it. writing is still difficult, but thats still microsoft's fault for keeping the way a dirty filesystem works a secret

---

### Post by dnccnd on 2006-06-16
I dont' really know what the /etc/fstab is!!! :confused: 

I don't even find this folder in the File Browser...

---

### Post by raptros-v76 on 2006-06-16
a "/" usually (in most sane filenaming policies) represents the directory paths
therefore
/etc/fstab
is a file called "fstab" which is in /etc

---

### Post by aysiu on 2006-06-16
You don't need to install *ntfsprogs* to read from it, or if you do, then it's already installed.

In other words--the default Ubuntu can read just fine from NTFS.

If it *is* NTFS, that is.

If it's FAT32, you can read from and write to it just fine.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) tells you everything you need to know.

---

### Post by dnccnd on 2006-06-16
I tried "sudo apt-get install ntfsprogs" but I still have the same problem.

Thanks for helping...

---

### Post by aysiu on 2006-06-16
[QUOTE=dnccnd]I dont' really know what the /etc/fstab is!!! :confused: 

I don't even find this folder in the File Browser...[/QUOTE]
Windows uses backslashes. Linux uses forward slashes.

/home/username/.mozilla

C:\Documents and Settings\username\Application Data\Mozilla Firefox

---

### Post by dnccnd on 2006-06-16
[QUOTE=raptros-v76]a "/" usually (in most sane filenaming policies) represents the directory paths
therefore
/etc/fstab
is a file called "fstab" which is in /etc[/QUOTE]

Ok, this is the content of the file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

