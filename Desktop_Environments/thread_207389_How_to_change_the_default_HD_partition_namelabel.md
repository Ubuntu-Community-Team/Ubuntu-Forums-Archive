---
title: "How to change the default HD partition name/label?"
date: 2006-07-01
forum: Desktop Environments
---

### Post by Redindian on 2006-07-01
I have Windows (sda1) and 2 linux OS's (sda2 and sda3) on my machine. Ubuntu on sda2 and FC5 on sda3. On my ubuntu desktop, the other linux partition is shown as 'sda3'. How do i change the default partition name/label 'sda3' to 'FC5' or something else? 
Thanks

---

### Post by tonyr on 2006-07-01
You can try using the utility **e2label** if the FC5 partition is type ext2/ext3, or **tune2fs**.
Neither one changed the displayed name for me, but I didn't chase them too far.

EDIT:  I changed **/etc/fstab** to use the **LABEL=<partition-label>** convention
(see man **fstab**).  The new label showed upf after I rebooted.  The new line in my fstab
looks like this:
```

LABEL=SpareOom  /media/hda9     ext2    defaults        0       2

```
I suggest unmounting the partition before changing the label name, and running the **e2label** or **tune2fs**
command with **sudo**.

---

### Post by Redindian on 2006-07-02
Thanks tonyr. 

I did further research in ubuntuforums, i found the solution like you replied above. Checkout this link: [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive) ...this is for USB drive but also the same for internal partitions. Have fun guys...Ubuntu rocks.

---

