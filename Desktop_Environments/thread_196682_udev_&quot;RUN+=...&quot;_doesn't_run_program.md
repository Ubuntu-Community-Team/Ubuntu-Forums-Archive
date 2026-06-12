---
title: "udev &quot;RUN+=...&quot; doesn't run program"
date: 2006-06-14
forum: Desktop Environments
---

### Post by pwyzorski on 2006-06-14
I have a rule in my udev directory with the following text:

KERNEL="usb*", SYSFS{product}="Vendor X", RUN+="brctl addif bridge0 %k ; ifconfig %k up"

It is intended to recognize when a USB network device from a certain vendor is hot plugged into the system and then bind it to a bridge. My device is recognized, and I can even rename it if I add the following; "NAME=VendX-%k". The problem is that my Run commands never get run and my device is never added to the bridge and I have no error codes.

udevtest also seems to indicated no programs being run as well -- output attached.

/etc/udev/rules.d$ udevtest /sys/class/net/usb1 net
main: looking at device '/class/net/usb1' from subsystem 'net'
main: opened class_dev->name='usb1'
wait_for_sysfs: file appeared after 0 loops
run_program: 'iftab_helper usb1'
run_program: '/lib/udev/iftab_helper' (stdout) 'usb1'
run_program: '/lib/udev/iftab_helper' returned with status 0
udev_rules_get_name: rule applied, 'usb1' becomes 'usb1'


I've reviewed as much documentation as I could find on the subject of udev -- yes I've studied "http://www.reactivated.net/writing_udev_rules.htm" at great length to no avail.


brctl is installed and working properly as I can do these commands manually and add the USB network device to the bridge.


Any additional info on this would be helpful.

~P

---

### Post by pwyzorski on 2006-06-14
Turns out you must have the full path to the program you want to run.

You also cannot have multiple commands in a single run statement.

The above script written correctly would look like:
ACTION=="add", KERNEL=="usb*", SYSFS{product}=="Vendor X", RUN+="/usr/sbin/brctl addif bridge0 %k"
ACTION=="add", KERNEL=="usb*", SYSFS{product}=="Vendor X", RUN+="/sbin/ifconfig %k up"

Info, just in case anyone else runs into this issue and can learn from my mistake...

---

