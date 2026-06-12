---
title: "Running external programs when USB drive is inserted"
date: 2006-08-30
forum: Desktop Environments
---

### Post by evquink on 2006-08-30
I am trying to get an external script to run when I insert one of my USB drives.  I have sucessfully used udev to create symlinks using information from [this page]("http://http://www.reactivated.net/writing_udev_rules.html") but I can't for the life of me get the following udev entry to run my script:

BUS=="usb", SYSFS{serial}=="09F11950C3904924", ACTION=="add", NAME="%k", SYMLINK="GTDWiki", GROUP="etg", OWNER="etg", MODE="0660", RUN+="/home/etg/my_script"

my_scipt is an executable shell script.

Any suggestions would be appreciated.

---

