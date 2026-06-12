---
title: "Automounting/writing a Windows HD"
date: 2005-08-09
forum: Desktop Environments
---

### Post by Curlydave on 2005-08-09
I've followed the Ubuntu wiki article on mounting a Windows HD and it works. (very useful for moving files and playing music directly off my windows HD) However, I have to mount the hd using a command "sudo mount /dev/sda1" every time I boot into Ubuntu or it won't let me use the HD. How can I get this to work automatically?

Also, I can read files on my Windows hd fine and copy them to my Linux HD, but I can't write to my Windows HD. How can I fix this? Thanks!

---

### Post by varunus on 2005-08-09
To automount NTFS on boot, add it to your fstab.  Follow the instructions here:
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

Unfortunately, due to the closed nature of NTFS, the opensource linux driver can't write to it.  There are two solutions to this:

1.  Paragon - Paragon is a company that sells an NTFS driver for linux.  You can purchase and use it if you want to.  You'd probably much rather get something for free though, I bet, so you can try

2.  Captive - Captive is a project very similar to ndiswrapper that uses windows' NTFS.sys file to read/write to NTFS in Linux.  Its a little slow, but it works, apparently.  I've never used it...good luck if you try it.
Here's the offical Captive site:
[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)
Here's a .deb package of captive that claims to be for Ubuntu and Debian:
[http://www.kruyt.org/?sub_item=46](http://www.kruyt.org/?sub_item=46)

I've never used it, and apparently there are some issues with it, but you can try it.  You need to unmount your drive manually, apparently, or you can cause problems; you can add something to the shutdown scripts to do this for you using update-rc.d, I guess.

---

### Post by Curlydave on 2005-08-09
It's still not automounting and I have to do the command. :(

I tried replacing the wiki's entry,  /dev/sda1        /mnt/winXP       ntfs       ro,auto,uid=1000,gid=1000 0 0

with that guide's, /dev/sda1       /mnt/winXP      ntfs    nls=utf8,umask=0222 0       0

The result's the same: it works but I have to use sudo mount /dev/sda1 whenever I restart. What's up? You'd think that the "auto" command in there would work...

Here's my fstab file: 
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /mnt/winXP      ntfs    nls=utf8,umask=0222 0       0
#/dev/sda1      /mnt/winXP      ntfs    ro,auto,uid=1000,gid=1000 0 0

I commented out the original command I had from the wiki.

---

### Post by varunus on 2005-08-10
That's very odd...Does dmesg say something right after you boot about mounting the NTFS drive?  Type dmesg | grep sda1 or dmesg | grep mnt or something to see...Maybe there's some other error.

---

### Post by mo_x on 2005-08-10
Looks like a SATA drive. Is the driver module loaded when the auto mounting is done? If not I think you should put it in /etc/modules.

---

