---
title: "Administrator mode only as root"
date: 2005-11-06
forum: Desktop Environments
---

### Post by Ralf on 2005-11-06
Hi, 

I just installed kubuntu the first time. The installation runs
really smooth :p 

I don't like that users have access to the Adminstrator Mode 
of the Control Center (kcontrol) in a multiuser enviroment 
using their own password. 

So I give a password to the root account by 'sudo passwd root'
and disable all sudo things for the admin-group in /etc/sudoers.

What changes in KDE has to be done, that the 'Administrator 
Mode ...' button of the Control Center ask the user for the 
root password and not for the user password? 
(which doesn't work anymore due to my modifications in  /etc/sudoers) 

Ralf

---

### Post by aysiu on 2005-11-06
My understanding is that if users are *not* in the sudoers file, they *cannot* access administrator mode.

---

