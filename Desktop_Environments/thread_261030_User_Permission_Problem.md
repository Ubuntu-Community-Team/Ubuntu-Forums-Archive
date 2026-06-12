---
title: "User Permission Problem"
date: 2006-09-19
forum: Desktop Environments
---

### Post by limiter on 2006-09-19
While creating an Admin account and downgrading a former admin account I accidentally was left with two accounts with no admin privledges.  

How can i give one of the accounts admin privledges back?

gnome login won't let me login as root, and both accounts don't have the admin menu options.

Thanks

---

### Post by CatKiller on 2006-09-19
If you boot from the Live cd, or boot in recovery mode, you'll be running as root. That should let you fix the problem. I believe that the solution is to add one of the users to the admin group, although I'm not entirely sure of the command to do so. It'll be something like **adduser <user> admin**, where <user> is the name of the user that you want to give privileges to.

---

### Post by limiter on 2006-09-19
I tried to boot from the live CD but I could not find any option to change any user permissions on the currently installed ubuntu.  Is there a boot option i should use with the live CD?

I tried to boot from recovery mode as well.
Recovery mode dumped me to root command line so i typed "startx gnome"
it returned with an error about some fonts not being properly installed.

Is there a configuration file i can edit from the command prompt to make these changes?  I first changed the user permissions through System>Administraition>Users>User Permissions in the gnome desktop.  

Thanks

---

### Post by skymt on 2006-09-19
Boot to recovery mode, then enter these commands:```
adduser *yourusername* admin
reboot
```You'll come back up to a graphical login, and the user *yourusername* will be sudo-enabled.

---

### Post by aysiu on 2006-09-19
An elaboration on skymt's advice:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

