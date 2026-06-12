---
title: "LVM ERROR group exported?"
date: 2006-09-23
forum: Desktop Environments
---

### Post by puccaso on 2006-09-23
ok, so i made a bummer..
i bought the damned freecom dvb-t usb stick
and it is being a pain so i went over to MCE for a few days... to see if i could get it working there (I HATE MYSQL, I CAN NEVER MAKE IT WORK SO I COULDNT USE MYTH..) anyway..

yea so..
my setup is..

hda1 - boot
hda2 - MCE/XPoo
hda3 - LVM  - 
lvm1 - home
lvm2 - root
lvm3 - swap.

so i booted in with an old dapper cd i had,
fdisked, boot deviced hda1, so the already install grub could just take over... and voila - it should have just booted, right? NO...

i got "incorrect operating system" something or other type of error..
so i went back in the with the dapper cd, so try and reinstall grub to the MBR... i thought i'd do it the fast way
and somewher eor other, i typed in the lvmexport command... 
and it said group "jt" exported.

so, ok - now - i'm tryna get back to into the system - via rescue option, i thought i'd chroot and install grub that way - 
but now i cant acccess my LVM groups

everything says group "jt" exported.. "jt" is my lvm group name btw.. but thats not important.


how do i import or undo what i've done
i cant stand windows
its so slow! grr.

plz help somebody!!!

also
even when i use
the debconf installer thing, the autoparted thingi wont read teh LVM... i mean i think the export messed something up
how do i undo the export??

any ideas?

---

