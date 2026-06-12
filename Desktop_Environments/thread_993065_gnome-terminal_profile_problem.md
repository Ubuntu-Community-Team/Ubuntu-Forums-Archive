---
title: "gnome-terminal profile problem"
date: 2008-11-25
forum: Desktop Environments
---

### Post by ramsesdm on 2008-11-25
Hi, yesterday i created a new user as a sudo user. When i open a terminal in the new user session it show only the "$" symbol and the tab key and the arrows keys to navigate across the history does'nt work.
I review my .bashrc file and everything seems to be fine. 
Any help?

---

### Post by scottkicksbutt on 2008-11-25
It looks like it's probably a permissions issue on your .bashrc. Try running:
ls -al ~/.bashrc

Which should produce:
-rwxr-x--- 1 yourusername yourusername 2940 2008-09-22 19:03 .bashrc

if the ownership is incorrect run the following as root:
chown yourusername:yourusername ~yourusername/.bashrc

or if the permissions are incorrect:
chmod 750 ~yourusername/.bashrc

---

### Post by ramsesdm on 2008-12-03
> **ramsesdm said:**
> Hi, yesterday i created a new user as a sudo user. When i open a terminal in the new user session it show only the "$" symbol and the tab key and the arrows keys to navigate across the history does'nt work.
I review my .bashrc file and everything seems to be fine. 
Any help?

Solved!! was the shell's path in my user account

---

