---
title: "usb problems virutal box 2.2.4"
date: 2009-06-04
forum: Desktop Environments
---

### Post by burntresistor on 2009-06-04
I just started trying to get Virtual box working and I can't seem to get the usb HD working, It detects that I have it connected to the computer in settings before I start VB. I unplug and replug the usb HD after I turn on VB. What else can I do to fix this I'm running VB in XP

---

### Post by mirons on 2009-06-04
I had a problem wit usb on vbox, too, don't know if it's the same. vbox detected the device in devices menu, but they were disabled. It was a permissions issue, fixed adding a line in /etc/fstab
here is the line
```
none /proc/bus/usb usbfs devgid=112,devmode=664 0 0

```
BTW: devgid is the GrouID of group vboxusers

---

### Post by beameup on 2009-06-04
Did you check the box in "Settings" > "USB" next to the drive?

See attached for an example. That worked with my TomTom. I have XP in a virtual machine.

---

### Post by WIGGMPk on 2009-06-04
Make sure your user is part of the vboxusers group, add it if its not, than restart and it should work fine.


Adding the line to /etc/fstab should not be neccessary. But that would be my next step if your already part of the vboxusers group. I would check the group settings first though.

---

### Post by burntresistor on 2009-06-05
> **mirons said:**
> I had a problem wit usb on vbox, too, don't know if it's the same. vbox detected the device in devices menu, but they were disabled. It was a permissions issue, fixed adding a line in /etc/fstab
here is the line
```
none /proc/bus/usb usbfs devgid=112,devmode=664 0 0

```
BTW: devgid is the GrouID of group vboxusers

What did you mean by groupID and how is it changed or checked to see if mine is right? the command didn't have permissions , also in usb settings all necessary usb boxes were checked

---

### Post by WIGGMPk on 2009-06-07
> **burntresistor said:**
> What did you mean by groupID and how is it changed or checked to see if mine is right? the command didn't have permissions , also in usb settings all necessary usb boxes were checked

You shouldnt need to do this...

Have you checked to see if your user is part of the vboxusers group??

I had the same issue before and adding my user to the group resolved it.

---

### Post by doomsword2001 on 2009-10-03
hey guys i have VB usb prob too.
i followed other guides which users repliy and say that works but i cant get it working.
1. my usb are not gray'ed out, they appear as normal.
2.  i right click and enable the usb.
3. win xp detects usb, installs drivers.
4. then xp freezes until i disable usb again.

i have added my self in group, i have the usb unmounted and enabled in VB.
any ideas? 
cant switch to vmware cause its kind of slow and i need xp for visual studio sto VB is my only solution :/

---

### Post by doomsword2001 on 2009-10-03
i have managed to get my printer working which was my main prob :)
my external hard disk is still not working :/ so its a hard disks prob i guess
so nvm

---

