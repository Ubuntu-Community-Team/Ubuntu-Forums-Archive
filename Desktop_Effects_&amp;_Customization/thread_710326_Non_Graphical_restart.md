---
title: "Non Graphical restart"
date: 2008-02-28
forum: Desktop Effects &amp; Customization
---

### Post by ericjensenddr on 2008-02-28
I am new to ubuntu, but have been using it exclusively for about 2 weeks.

I have a notebook and wanted to run a 2nd monitor, 17 inch LCD.

I hooked it up and the machine decided ro go into low graphics mode. Then I adjusted the second monitor and rebooted.

I am now getting the non-graphical boot with a few messages:
kinit:name_to_dev_t (/dev/disk/by-uuid/...)=sda(8,5)
kinit trying to resume from /dev/disk/by-uuid..
kinit: No resume image, doing normal boot

Any suggestions?

I now have data on this I need ot access...is there a "repair" option?

Eric

---

### Post by PinkFloyd102489 on 2008-02-28
Open up the file menu.lst in /boot/grub.


Check to see if "quiet" is present under defoptions and alt options. If not, add it. Then do this:

```

#Updating grub
sudo update-grub

#Regenerating linux image
sudo update-initramfs

```

---

