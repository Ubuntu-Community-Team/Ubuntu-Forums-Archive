---
title: "USB Drive mounting problem."
date: 2006-01-28
forum: Desktop Environments
---

### Post by irv on 2006-01-28
I have two computers running Ubuntu Linux, and I would like to move a USB hard drive from one computer to the other. When I plug the USB hard drive into the first computer it see it and mounts it automatically. (no problems). When I do the same on the other, it sees it but will not mount even if I do it manually.  
			irv@wabasha-server:~$ mount sdb1
			mount: can't find sdb1 in /etc/fstab or /etc/mtab
			irv@wabasha-server:~$

The disks setup screen after plugging in the drive lists the drive as there, but If I try to “Enable” on the Status, it will not let me. If I select the Change button it wants me to brows for the device access path, with is not listed anywhere.

I have the system set to automatically mount any new removable drives when hotpluged.

 I am not sure what's going on?
Has anyone else had this problem?
Thanks

---

### Post by cwaldbieser on 2006-01-28
[QUOTE=irv]I have two computers running Ubuntu Linux, and I would like to move a USB hard drive from one computer to the other. When I plug the USB hard drive into the first computer it see it and mounts it automatically. (no problems). When I do the same on the other, it sees it but will not mount even if I do it manually.  
			irv@wabasha-server:~$ mount sdb1
			mount: can't find sdb1 in /etc/fstab or /etc/mtab
			irv@wabasha-server:~$

The disks setup screen after plugging in the drive lists the drive as there, but If I try to “Enable” on the Status, it will not let me. If I select the Change button it wants me to brows for the device access path, with is not listed anywhere.

I have the system set to automatically mount any new removable drives when hotpluged.

 I am not sure what's going on?
Has anyone else had this problem?
Thanks[/QUOTE]
Try using the "pmount" command to mount it and see if that works.  If not, try adding an entry for the drive in your /etc/fstab.  Make sure there is an existing mount point (folder) for it in this last case.

---

### Post by irv on 2006-01-28
Thanks cwaldbieser, I tried
irv@wabasha-server:~$ pmount /dev/sdc1 and it mounted the drive.
Thanks again.

---

### Post by kevinmthor on 2006-02-01
hi forum,

i am trying to mount my USB stick but, it is not working. when i put it in the usb drive, i get the light to come on but, it will not auto mount. i tried to mount and pmount the /dev/sda1 but, no such driver exists in my /dev directory. 

i tried editing the /etc/fstab with:

/dev/sda1    /media/usbdisk    auto   user, auto, sync   0    0

when i did this, the USB Drive showed up on my computer - file browser but, i could not get into it. my error was:

mount: mount point /media/usbdisk does not exist

when i did ls -l /media sure enough, i only had cd and floppy, no usbdisk.

as a matter of fact, when i ls -l /dev sd* nothing shows up as well.

any suggestions?

thanks

k

---

### Post by irv on 2006-02-01
Do you have hotplug installed. It is in Synaptic Package Manager?

---

### Post by kevinmthor on 2006-02-01
hi irv,

yes, hotplug is installed, version 0.0.20040329-16ub.

k

---

### Post by kevinmthor on 2006-02-02
so i figured out i need a folder and a symbolic link in the /media folder but, how do i connect to /dev/sda1 if it is not already in the /dev folder?

can i use something else from /dev? if not, how do i create /dev/sda1?

k

---

### Post by jazzgossen on 2006-02-10
Are you sure that your USB stick should be /dev/sda1? On my system, it is /dev/sdb. Try connecting the stick, and type "sudo fdisk -l /dev/sdb" to see if the drive shows up there. Maybe that can give a hint as to what's wrong.

---

