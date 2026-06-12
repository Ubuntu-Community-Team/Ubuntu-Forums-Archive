---
title: "windows partition accessing (Solved)"
date: 2005-10-17
forum: Desktop Environments
---

### Post by tellyousomeday on 2005-10-17
how do you  access windows partitions?

---

### Post by seldenthuis on 2005-10-17
If Ubuntu detected your partitions while installing, you should be able to find them under /media/hd... If not, you have to find the device nodes corresponding to your windows partitions (/dev/hda1 for example). You can then create a folder under /media and add the partition to /etc/fstab.

For example:

sudo mkdir /media/windows
sudo gedit /etc/fstab
Add the following line at the end of the file:
/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0

After a reboot, the windows partition /dev/hda1 is mounted under /media/windows and you can access it like any other folder.

---

### Post by fortytwo on 2005-10-17
EDIT: beaten by a better post :)

---

### Post by tellyousomeday on 2005-10-18
Thank You!!!

---

