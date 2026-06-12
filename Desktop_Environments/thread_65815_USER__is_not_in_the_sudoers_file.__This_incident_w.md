---
title: "USER  is not in the sudoers file.  This incident will be reported.????"
date: 2005-09-15
forum: Desktop Environments
---

### Post by StemCell00 on 2005-09-15
im trying to mount an NTFS partion of my hdd. using the unoffical guide i goto the terminal and type..(im a linux newb)

======================
stemcell@StemCell:~$ sudo fdisk -l
Password:
stemcell is not in the sudoers file.  This incident will be reported.
stemcell@StemCell:~$
======================

so...the question is, how do I edit the sudoers file - I double click on it & it says "Couldn't Display "/etc/sudoers".

---

### Post by zAo on 2005-09-15
In /etc/sudoers you can find the groupname you need to be a member of (I think that's %admin). Add yourself to that group (failsafe?) and sudo!

---

### Post by roblubbers on 2005-09-15
if your able to get into the roor account (if you've created one) you can execute visudo to edit the sudoers file

---

