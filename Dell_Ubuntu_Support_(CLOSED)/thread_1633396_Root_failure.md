---
title: "Root failure"
date: 2010-11-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tngcg1 on 2010-11-29
I have a dell mini, 2 days ago I tried to boot up and got the following: 

mount: mounting /dev on /root/dev failed: No such file or directory

mount: mounting /sys on /root/sys failed: No such file or directory

mount: mounting /proc on /root/proc failed: No such file or directory

Target filesystem doesn't have /sbin/int.

[    1.412073] usb 5-1: new full speed usb device using uhci_hcd and address 2 
No init found. Try passing init= bootarg.

I have tried bypassing the initial boot  but not sure what to do. Does the root need to be reinstalled and can I do that by tethering to another computer? Help!

---

### Post by mikewhatever on 2010-11-29
The error basically says that there is no root partition. Possible causes are boot loader bugs, UUID change, disk failure. Can you boot from live usb and post the output of **sudo fdisk -l**.

---

