---
title: "partition question"
date: 2006-08-22
forum: Desktop Environments
---

### Post by jazzman14 on 2006-08-22
On a hardrive I had one partition of just ubuntu, i downloaded the gpart and created a nfts partition so that I can install windows, I installed windows on that partition, but when the computer starts it goes through the usual partition and runs ubuntu, I went into the bios but all you can select is the hard drive, not the partition. In gpart, I set the partition with windows as the boot partition, still ubuntu boots up, how can I choose which i want to load or what do i do? Thanks.

---

### Post by lateralchaos on 2006-08-22
try adding something like this to the end of the /boot/grub/menu.lst file:

```
sudo gedit /boot/grub/menu.lst
```

title         Windows 95/98/NT/2000
root          (hd0,0)
makeactive
chainloader   +1\

if the windoze partition is the second partition replace hd0,0 with hd0,1

---

### Post by BlaineM on 2006-08-25
type into the terminal sudo gedit /boot/grub/menu.lst
then type in your password.
this will open the file menu.lst.
within the top part of the screen you will see the option that looks like

# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

Notice that the default line does not have a # before it, this means that your grub loader will look at this line to see what you want it to do.  There are a lot of different options that you can change in this file such as hidden menu options and colors and such.  Read the documentation about this under the system help and it will explain this to you also.

Anyway, change the default to +1 instead of 0, this will make grub boot to whatever is in the place for plus one, which is XP for me.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1

This is what is at the bottom which points to where Windows is stored.  Read the documentation for this.  A lot of answers to the questions that I have had have been answered by the docs, but not all of them.

---

