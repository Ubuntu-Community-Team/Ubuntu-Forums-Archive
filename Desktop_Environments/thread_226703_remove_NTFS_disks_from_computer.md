---
title: "remove NTFS disks from computer:///"
date: 2006-07-31
forum: Desktop Environments
---

### Post by Indrek on 2006-07-31
how i do that? These additional disks are not needed. computer:/// is opened from nautilus.

quick reply please!

---

### Post by x64Jimbo on 2006-07-31
Do you mean that you want to delete the partitions entirely or unmap them from the system's filesystem map?

---

### Post by endfx on 2006-07-31
You would probably want to edit /etc/fstab and comment out the line that mounts your ntfs disks. Now they won't be mounted when you start your computer and probably won't be in computer:///

---

### Post by x64Jimbo on 2006-07-31
Just for clarification, to comment out a line of code, put a pound sign in front of it like this:
```
Regular code
# commented-out code
```
And to edit your fstab, run this command:
sudo gedit /etc/fstab

---

### Post by Indrek on 2006-07-31
i need to get off ubuntus automount from windows partitutions. I don't need these.
atm if click on partitutions i get:
error: device /dev/hda1 is not removable
error: device /dev/hdb1 is not removable

how i remove these then?

Note: I have already removed lines from fstab.

---

