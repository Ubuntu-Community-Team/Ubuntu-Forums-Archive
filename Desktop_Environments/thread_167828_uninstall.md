---
title: "uninstall"
date: 2006-04-29
forum: Desktop Environments
---

### Post by fotoid on 2006-04-29
I have 2 hard drives on my comp.windows xp is installed on one and linux ubuntu is installed on the other. when I reboot my system it goes to linus as default. My queestion is how do I uninstall linux from the one hd. it uses Grub to loadup. Don't know if I need to post anymore info but I will if need be. Thanks in advance for all and any help.

---

### Post by sYs^ on 2006-04-30
If I were you, I would change the first boot device in BIOS to the hdd with Windows then I would install PartitionMagic on Windows and with that you can easily remove the linux partitions from the other hdd.

By the way I wouldn't delete Linux. :>

---

### Post by fotoid on 2006-04-30
ok, I'm not real computer savvy but BIOS is whenn I hit the delete key when booting up?? problem is I don't see the other hard drive when I do that.

---

### Post by Sef on 2006-05-01
> BIOS is whenn I hit the delete key when booting up?? 

When your computer first starts, it tells you what to push to get into the BIOS.  Usually it is either F2, esc, or delete.

---

### Post by raovq on 2006-05-01
just mash the f keys during startup, before windows or linux starts. you will get a blue screen (or some vibrant colour) where you can change a few things. you want something along the lines of boot order or device boot or something. its pretty self explanitory. just swap the hardrives to boot from the other.

---

### Post by fotoid on 2006-05-01
ok when I hit the ESC key I get a screen that says

one-time Boot

cd rom
Diskett grive A
HDD1 wdcWd400


when I hit the delete key I get

Primary Drive 0 performance

primary Drive 1 Quiet

then it had a Boot order but only shows

CD Rom
Floppy
Harddrive C


( I mashed the f-keys and had to buy a new keyboard, that didn't work)

---

### Post by fotoid on 2006-05-07
So I guess I'm out of luck ??? no more help? Thanks for he responses anyway.

---

### Post by SkyNet2029 on 2006-05-08
The simplest way to do this would be to run the command of 'FIXMBR' from a windows recovery console, the last prompt during bootup of the installation cd (Windows CD of course). This forces a rewrite of the MasterBootRecord to the target partition (The one you selected when it asks which Windows installation would you like to log into). From there a simple reboot is needed, called from a command line, with 'EXIT' . 

This assumes you have a copy of your install CD for windows.. 

If you have decided that Ubuntu is for you, then editing your Grub menu is also a possibility, to allow for Grub to give you a choice of booting into Windows or Ubuntu.  

In Terminal as root: 

#nano /boot/grub/menu.lst

I almost forgot.. Use compmgmt.msc from <Run> prompt then Disk Management to reformat that second drive. (After having made a backup of things you needed, of course)

Hopefully you go with the option of editing your Grub Menu, as Ubuntu is superior. ;-)

---

