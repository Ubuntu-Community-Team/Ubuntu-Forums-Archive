---
title: "PC Won't boot, file system damaged?"
date: 2009-10-15
forum: Desktop Environments
---

### Post by RobertHamilton on 2009-10-15
Hi,
My computer was booting fine about an hour ago but since then I have edited the menu.lst and the usplash with 'Startup manager' because I was following a guide to make my desktop look like MAC OSX Leopards'. I had actually already done this but the grub loader screen hadn't changed; so I redid this part of the guide. After I had done that I rebooted and got the error "undefined video mode: 318" or something like that.. I can click Enter to choose another video mode or Space to continue. So, if I continue, it loads Ubuntu but in the command line without the Graphical Interface. It also says this, above where I log in .. 
"
usplash: No usable theme found for 640x480
screen init failed
19+0 records in
19+0 records out
kinit:name_to_dev_t(/dev/disk/by-uuid/-blahblahblahblah(252,4)
kinit:trying to resume from /dev/disk/by-uuid/blahblahblah
kinit: No resume image, doing normal boot
"

Plus, in the command line if I type 'Sudo edit /boot/grub/menu.lst/' it says it does not exist. I also can't find the stuff in my Home folder by using cd and ls commands.
So now here I am using the Live CD, given up on trying to repair my system but I still want to recover my data (some videos, music and important documents). I've tried Testdisk but it says 'No file found, filesystem seems damaged.' :confused:

The only difference I had made to my computer was adding the line 'vga=792' or something to the menu.lst and uninstalling/configuring Splashy and Usplash. I don't see how my file system could possibly have been damaged by these few tweaks. :S I want to install Karmic Koala now but not without getting my data back first. 

Please can someone help?

My system as follows
> Ubuntu Jaunty Jackelope 9.10
m/b: P5Q Deluxe
cpu: Intel Q6600 Quad 3.6Ghz
mem: 4Gb OCZ kit
gfx: Gigabyte HD 4850 (ATI)
hdd: Raid0 (640gb+640gb) WD Caviers
EDIT: I've tried recovery from the GRUB loader

---

### Post by RobertHamilton on 2009-10-15
bump

---

### Post by RobertHamilton on 2009-10-15
Anyone? :(

---

### Post by sisco311 on 2009-10-15
Check the partitions for errors. Use Gnome Partition Editor.
Press Alt+F2 and type: ```
gksu gparted
```

---

### Post by RobertHamilton on 2009-10-15
argh. it says unallocated. I guess that's it then. Time to install karmic koala :(

---

### Post by sisco311 on 2009-10-15
> **RobertHamilton said:**
> argh. it says unallocated. I guess that's it then. Time to install karmic koala :(

Your data should be still there:
[https://help.ubuntu.com/community/DataRecovery]("https://help.ubuntu.com/community/DataRecovery")

---

