---
title: "Cannot access sudo commands"
date: 2005-10-01
forum: Desktop Environments
---

### Post by jeremy24 on 2005-10-01
I have somehow managed to get myself off the sudoers file, so I cannot access any administrative options and cannot use sudo commands. I have managed to change the root password, but I still cannot log in as the root user. I cant log in as any user other than the one without access. Any help would be appreciated.

---

### Post by jeremy24 on 2005-10-01
Ok, I can now access the root account in the console, but I still cant access any administrative options from my full account. I can get a console looking like this:
__________________________________________________
root@ubuntu:~ #
__________________________________________________
But then if I try to edit the sudoers file from this ^ line I get get an error like this:
__________________________________________________
root@ubuntu:~ # export EDITOR=gedit && sudo visudo

(gedit:7791): Gtk-WARNING **: cannot open display:
visudo: sudoers file unchanged
__________________________________________________
Any help would be appreciated, Thanks.

---

