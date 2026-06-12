---
title: "Cannot add hard drive to VMware. Insufficient permission."
date: 2006-08-31
forum: Desktop Environments
---

### Post by titancomputing on 2006-08-31
I've got VMware finally installed on my Dapper Drake with XP loading and booting. Now my problem is I'm trying to add a 300 GB physical NTFS disk I have mounted in Linux to my VMware session. Every time I go through the process to add it, I get the message that I have insufficient privelages. How can I get the appropriate ones so that I can view my drive in XP? And finally, is there a way to drag and drop files from my desktop to my virtual machine?

---

### Post by fk4n on 2006-08-31
try add sudo infront of the command. or type in sudo -i to gain root.

---

### Post by ewerx on 2006-09-03
I would also like to mount an NTFS partition in my vmware virtual machine (running XP installed on a virtual disk). The drive is /dev/sdb but when I try to add physical disk and point to this drive I get permission denied.

I don't think it's safe to always run vmware as root, so I am hoping there is a way around that.

Also, Ubuntu has the partition mounted read-only (I have not tried the ntfs-3g stuff yet), so if eventually I manage to mount the NTFS partition in vmware, will the virtual machine have read/write access or read-only?

---

### Post by anaconda on 2006-09-03
I think the wirtual machine will have read-only rights, because that is what your ubuntu-box has.

And I have understood that the easiest way to get your hd to work in ubuntu is to install samba, and use the hd as a network share. I dont think mounting works..

that is because yout virtual-machine is completely separated from your real machine.. execpt for the removable drives..

---

