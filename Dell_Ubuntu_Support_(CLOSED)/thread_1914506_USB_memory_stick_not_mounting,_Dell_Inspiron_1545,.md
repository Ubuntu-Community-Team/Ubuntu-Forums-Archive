---
title: "USB memory stick not mounting, Dell Inspiron 1545, Ubuntu."
date: 2012-01-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lornt78 on 2012-01-24
:confused::confused:I've got the latest Ubuntu on Dell Inspiron 1545. My USB stick has stopped showing up when I plug it in. The USB stick works in other computers, and other USB devices work in my laptop. Any ideas? Bios? (Actually, I don't even know what that is.):confused:

Free popcorn:popcorn: to whoever can solve this.

---

### Post by lucas8880 on 2012-01-25
Hi, I had the same issue.

The way I fixed this is by adding a line to grubs configuration file.
try:[INDENT]         sudo gedit /etc/grub.conf[/INDENT]then add the line:[INDENT]     GRUB_CMDLINE_LINUX="acpi=off"
[/INDENT]then save the configuration file and update grub with:[INDENT]         sudo update-grub
[/INDENT]then try rebooting.  This works for me, I hope it helps you aswell.

This is the post I got my information from in case you want to look into it:

[https://answers.launchpad.net/ubuntu/+source/util-linux/+question/176732](https://answers.launchpad.net/ubuntu/+source/util-linux/+question/176732)

---

### Post by lornt78 on 2012-01-31
Actually, I managed to get it working by formatting the memory stick. Don't know why this was necessary, but it worked.

---

### Post by lucas8880 on 2012-02-01
Lol, okay.  Maybe the usb was formatted in an unknown filesystem?
Any way, I am glad its working for you ;)

---

