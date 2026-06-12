---
title: "How to Install Dapper in a external Hard drive ?"
date: 2006-09-28
forum: Desktop Environments
---

### Post by ss0007 on 2006-09-28
Hi ,
Last night, i tried to install Dapper in my secondary hard disk (IDE device)
connected via USB port. When the installer reached the partioning setup , i couldnt format any partitions in the HD. I could see a lock icon beside the drives partiotions . When i chose resizing and format a partition and finally push the Apply button, an error popped out telling unable to resize the partition. 

It seems that Partition editor is trying to unmount the partition before resizing physically. I could see the usbdrive disk icon in my desktop disappearing and appearing back again. 

Is there any way i can install Dapper in an external HD ?

Thanks.

---

### Post by bernied on 2006-09-28
If the installer won't work for you, you can do a more manual install using debootstrap. Look here:
[http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html](http://ftp.ubuntulinux.org/ubuntu/dists/warty/main/installer-i386/current/doc/manual/en/apcs03.html)
Don't do this if it is your first linux install, it will probably need a bit of tweaking.

My approach would be a bit different to the order that the installer takes, because I think the most difficult bit is getting the usb drive to boot. If it doesn't boot, is there any point having the ubuntu on it?

So, if it were me, doing all of this from a linux live-cd (doesn't matter which one, as long as it has fdisk and grub on it - most do - and will get you onto the internet):
1. partition usb drive using fdisk
2. install grub on usb drive
3. create a menu.lst in the grub root directory that will boot something else (other linux, windows, cd, whatever)
4. check that you can boot to the usb drive - critical step, if you can't boot onto the drive you can't run an OS from it. Even if you can't boot directly to the drive you could boot the usb from the hard drive, or from a floppy, but this is probably just as tricky and more complex.
5. do install from where that link starts

And seek other opinion before taking mine, there may be a much simpler way.

---

### Post by Kateikyoushi on 2006-09-28
Some people could install breezy on external hard drive then upgraded to dapper. [Link.]("http://ubuntuforums.org/showthread.php?t=80811")

---

### Post by ss0007 on 2006-09-28
wow, but tht's a hard way to do it ...
I am looking for directly install it  or 
else i can connect to an IDE port , install thr, and change the 
device parameters to continue in usb drive

---

