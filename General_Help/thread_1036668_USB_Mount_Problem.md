---
title: "USB Mount Problem"
date: 2009-01-11
forum: General Help
---

### Post by weiqiang on 2009-01-11
I'm running Ubuntu 8.04, everytime I try to automount a usb drive, I get the following message (in attachment), anybody seen this?

---

### Post by mikewhatever on 2009-01-11
To automount a partition, one usually adds a line for it to fstab. How do you do it?

---

### Post by weiqiang on 2009-01-11
I dont think i added that line...can you privide more info on that? Here is what my fstab looks like

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ab7f4f99-0158-4c10-acca-91442242c9ce /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6badf9fe-91d6-466b-a804-bddc66a5e50b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/hdd1 /home ext3 nodev,nosuid 0 2

---

