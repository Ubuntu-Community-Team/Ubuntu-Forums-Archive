---
title: "Can't launch admin apps as new user"
date: 2006-07-17
forum: Desktop Environments
---

### Post by DamnDirtyApe on 2006-07-17
I've performed the following steps on my new 6.06 install:

[LIST]
[*]Created a new user from the console
[*]Set the password for the new user
[*]Edited /etc/group and added the user to the "admin" group
[/LIST]

When I launch Synaptic from the menus and enter my password, it get's rejected (I get an error stating that I have the wrong password).  However, if I open a console and type "sudo synaptic", I can run it fine.  Any ideas on what would cause that???

Thanks for your help.

---

### Post by codejunkie on 2006-07-17
> **DamnDirtyApe said:**
> I've performed the following steps on my new 6.06 install:[LIST]
[*]Created a new user from the console
[*]Set the password for the new user
[*]Edited /etc/group and added the user to the "admin" group[/LIST]When I launch Synaptic from the menus and enter my password, it get's rejected (I get an error stating that I have the wrong password).  However, if I open a console and type "sudo synaptic", I can run it fine.  Any ideas on what would cause that???

Thanks for your help.
try adding your new user to the sudoers file and see if this fixes it,
login with the user account that is working correctly, and run
```
export EDITOR=gedit && sudo visudo
``` in a terminal this will open a text file, add your new user to the bottom of the file like this
```
yournewusername ALL=(ALL) ALL
```save the file logout and try the new account again.

---

