---
title: "Create boot disk in Ubuntu 7.04"
date: 2007-09-30
forum: Desktop Environments
---

### Post by Micik on 2007-09-30
Hello, I need to create boot and root disks in linux. At home,  I have Ubuntu 7.04, but at work there is one machine on which is red hat 6.0 is installed and which has booting problems. I'm not able (not permitted) to update to newere linux distribution. I have found procedure for boot disk and want to test at home. However, I'm having problems...
Here's procedure:

1. 	mke2fs /dev/fd0
2. 	mount -t ext2 /dev/fd0 /mnt
3. 	cp -dp /boot/* /mnt
4. Create a new lilo.conf on the floppy and add these lines:
	boot = /dev/fd0
	root = /dev/hda1
5. Install lilo on floppy with:
	/sbin/lilo -C /mnt/lilo.conf

But problem is how to create file on floppy disk under console in linux.
I tried to go there cd /dev/fd0 but I'm getting error message that fd0 is not directory.
How to make and edit file on floppy disk?
Thanks

---

### Post by arang on 2007-09-30
well it seems u must do "cd /mnt" cos as u can see u mounted the device fd0 into /mnt, so just do that cd /mnt and do ur lilo.conf editing there thats all

---

