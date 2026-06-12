---
title: "Grub"
date: 2009-04-12
forum: General Help
---

### Post by lafleur on 2009-04-12
Hey,

I am fairly new to ubuntu. Anyway i have been editing the grub today. I organised like this:

MS OS's:
Windows XP
Linux OS's:
Ubuntu 8.10

At the top is a title (MS OS's) and that is selected first. I am wondering without removing the title how I can select an OS so it is default?

Thanks.

---

### Post by statistic on 2009-04-12
If you read your /boot/grub/menu.lst you'll find near the top

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.

So just default to the appropriate menu number.
eg. Adding the line

default 1

should boot your Windows XP by default.

---

