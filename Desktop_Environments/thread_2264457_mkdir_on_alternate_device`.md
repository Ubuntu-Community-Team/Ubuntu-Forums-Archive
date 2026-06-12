---
title: "mkdir on alternate device`"
date: 2015-02-07
forum: Desktop Environments
---

### Post by Daniel_Devor on 2015-02-07
My computer has two hard drives with the operating system on the first  and a second 400Gb drive. I have easily made folders (ie. directories) on the first device but I do not understand how to do so on the second. I have tried a variety of methods to address the second device with mkdir but none seem to work. Help will be appreciated.

---

### Post by yancek on 2015-02-07
You need root privileges for most anything outside the /home/user directory so you would need to prefix the mkdir command with sudo:  sudo mkdir ???
What type of filesystem is it, Linux, windows?

---

### Post by ajgreeny on 2015-02-07
Yes, you will need ```
sudo mkdir /mountpoint/of/disk/partitions
``` to do that, so you need to find that disk's mountpoint first.

With the disk is mounted, which you can do by double clicking on its icon in the left hand pane of the filemanager, show us the output of terminal commands
```
sudo fdisk -l
mount
```

---

