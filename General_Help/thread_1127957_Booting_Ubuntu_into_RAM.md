---
title: "Booting Ubuntu into RAM"
date: 2009-04-17
forum: General Help
---

### Post by xris_xcess on 2009-04-17
Hi:

I have tried to follow this ( [http://ubuntuforums.org/showthread.php?t=707230](http://ubuntuforums.org/showthread.php?t=707230) ) how-to to set up an ALL in ram system.

I´ve followed all the instructions, but when I boot it up I get:

/init: line 191: could not open /dev/sda: no medium found... 

and several that read the same (with sdb, sdc, cdrom, etc)

I'm still looking, but could it be that I'm running intrepid 8.10, while the guide seems to have been done while using 7.10 or 8.04.

Has anyone tried this and got it to work sucessfully?

I'm trying this in combination with pxe-booting and NFS home folders and would really like to compare it to the regular nfs-root method.

Thanks.

---

### Post by xris_xcess on 2009-04-17
Just posting the actual error messages. At the end of the first part, the system drops into a busybox shell. Then I type exit to see if it will actually boot... but no luck there.

It would seem that some part of live-initramfs is set to look for the system on the cdrom, when in fact I want it to boot from the HD, and eventually over the network.

---

### Post by jbrown96 on 2009-04-17
I have the exact same problem with 8.10. I'm backing up my data now, and I'm going to give it a try with 9.04 tomorrow. Will let you know if I find anything.

---

### Post by xris_xcess on 2009-04-17
Well... I'm making some progress, but not what exactly what I need.

I't seems there is a bug in either the live-initramfs or initramfs package.

I tried to do this all over again on another machine and after installing live-initramfs, I can't rebuild my initrd.img. I get an error:

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.28-11-generic
cpio: ./bin/udevinfo: Cannot stat: No such file or directory
update-initramfs: failed for /boot/initrd.img-2.6.28-11-generic


Now this did not happen before I installed live-initramfs, so it has to be linked. I see there is an udev-extras package. Unfortunately, since dpkg didn't finish sucessfully with the previous install, I can't install it and neither remove live-initramfs!!!!

Any ideas? I'm off to check the bug list!

---

### Post by xris_xcess on 2009-04-22
Found a launchpad entry with a reference to live-initramfs. Reference to .sbin/udevinfo is incorect. It seems that it should point to udevadm.

I changed it manually and tried to rebuild initramfs. It finished fine, but when I re-tried the live system, no luck.

Im still not sure if they are linked, but it seems odd that no one had picked up this one before... unless of course,  in my custom install Im missing some extra packages .-)

---

