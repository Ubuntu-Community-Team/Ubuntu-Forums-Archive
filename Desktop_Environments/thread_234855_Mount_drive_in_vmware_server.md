---
title: "Mount drive in vmware server"
date: 2006-08-12
forum: Desktop Environments
---

### Post by CuBone on 2006-08-12
I run vmware server on Ubuntu 6.06. On the virtual machine I installed Win XP pro. So far so good (Actually it works great). But now to the problem. I want to have direct acess to one of my HD partitions (on the same physical computer as the virtual machine). I can share it on samba and access it that way but its terribly slow. So in the device settings I added the partition so that the vm could access it direct but when i power it on I get this message
Code:

Cannot open the disk '/var/lib/vmware/Virtual Machines/Windows XP Professional/Windows XP Professional-1.vmdk' or one of the snapshot disks it depends on. Reason: Insufficient permission to access file.

and then it won't start.

Does anyone now how I can change the permissions so I can access the partition?

---

### Post by donad on 2006-09-27
Well its been a month since your last post... Im having the same problem.  I thought it was a permissions problem because the disk I wanted to mount had both a fat and ntfs partition.  So I formatted it to one big ext3 partition but still get the insufficient "permissions to access" file when I try to add it to the vm.  The drive is writable by my user and has 777 permissions but i still cant add.  Is there anyone who has gotten around this?

---

### Post by kieran.campbell on 2007-01-14
I have the same problem with VMware on Edgy - I kind of got round it by adding the disks while running VMware as root...
```
gksudo vmware
```
then adding the disks in from there. Now I can run VMware as my own user and XP boots up, although I still get an error message that says 'Insufficient permission to access file' for each of the disks that I add, but these don't seem to hinder the ability of the virtual XP to use these disks.

---

