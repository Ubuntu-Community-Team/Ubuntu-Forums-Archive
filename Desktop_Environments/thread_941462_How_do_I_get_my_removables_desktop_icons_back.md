---
title: "How do I get my removables desktop icons back?"
date: 2008-10-08
forum: Desktop Environments
---

### Post by serafim on 2008-10-08
I wanted to test how to write udev rules so I fiddled around a bit with my eeexbuntu desktop and added new udev rules in a new file: 
/etc/udev/rules.d/55-my-settings.rules containing

BUS=="usb", KERNEL=="sd*", SYSFS{serial}=="146030377350", NAME="sdcard1", OPTIONS+="last_rule", RUN+="/bin/mount /dev/sdcard1"

BUS=="usb", KERNEL=="sd*", SYSFS{serial}=="0000187115723302", NAME="stick1", OPTIONS+="last_rule", RUN+="/bin/mount /dev/stick1"

BUS=="usb", KERNEL=="sd*", SYSFS{serial}=="5B8804000141", NAME="stick2", OPTIONS+="last_rule", RUN+="/bin/mount /dev/stick2"

and new rules in /etc/fstab:
/dev/sdcard1	/home/serafim/work  ext2 rw,owner,user
/dev/stick1	/media/cruzer	    ext2 rw,owner,user
/dev/stick2	/media/datatraveler ext2 rw,owner,user

It all works as a charm except that the icons don't appear on the desktop any more. Can I fix it? I tried all the common stuff with desktop settings an so on. The icons do appear if the sticks are present when starting the computer but not if I plug them in while the pc is running.

I really would like to umount them with the popup menu when right clicking the icons

---

