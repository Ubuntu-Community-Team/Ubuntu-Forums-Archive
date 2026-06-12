---
title: "Synaptic+Add/Remove Programs gone?"
date: 2006-06-08
forum: Desktop Environments
---

### Post by neoaddict on 2006-06-08
Hello,

I just upgraded from Breezy to Dapper and must say I'm impressed, except for a few little problems:

1) Synaptic is gone from the System -> Admin menu.

2) Add/Remove programs is also gone.

3) The System -> Admin menu seems unusually small.

Thanks for any help.

---

### Post by Ryutatsu on 2006-06-08
That's really strange I just did the same thing (upgrade from Breezy to Dapper) and I still have usable add and remove programs as well as synaptic. Both are in there usual places. Try "sudo apt-get install synaptic" and "sudo apt-get install gnome-app-install" no quotes
You also might have to use the menu editor to get them back in the gnome panel.

---

### Post by neoaddict on 2006-06-08
There's a menu editor for the Systems menu?  I've only seen the Applications Menu Editor.

Just reinstalled synaptic, the debi thingy says that synaptic is conflicting with synaptic.  o_O

**EDIT:** Edited the menu for Systems, Synaptic wasn't listed under Administration.

---

### Post by Erl1d on 2006-06-08
A friend of mine had the same problem after an upgrade, and in that case the user (for some reason???) had lost all its rights (check this with the command "groups" in the terminal, your user should be member of the admin group). I solved this problem by booting from the livecd, opening a terminal and then something like this (if i remember correctly).
```
sudo mount /dev/hda1 /mnt
sudo mount -t proc none /mnt/proc
sudo chroot /mnt
addgroup username admin
exit
umount /mnt/{,proc}
```
Remember /dev/hda1 with the correct partition, and username with your username. This will add the user to the admin group which will give you sudo rights so that you can add yourself to other groups with the gnome usermanager.

---

### Post by neoaddict on 2006-06-08
The problem was easy to fix (sorta):

I typed in adduser root root in Terminal (yes, I know about the security risk of using the root user in the root group, so please no lectures) and using the Deskbar, I opened up Users and Groups (that thing really saved my life there :D - those Ubuntu developers should really get some prizes for the GUI thinking there) and enabled all of the things on the third tab of user properties.

Restarted computer and all was fine.  XD

Dapper is humming along merrily.  :D

---

