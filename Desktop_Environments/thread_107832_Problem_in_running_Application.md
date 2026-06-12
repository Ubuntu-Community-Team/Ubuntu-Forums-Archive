---
title: "Problem in running Application"
date: 2005-12-24
forum: Desktop Environments
---

### Post by mayankgarg1 on 2005-12-24
Hi I have installed 5.10 version
and Created one user in group "root"
after login with this user,System ask for password for every application and go silent after entering password of root.
Even synaptic and users-admin, network-admin also can not be run with this user right.
I have also used run as different user option but in vein.system gets silent after entering password.
Please help me urgently.

---

### Post by briancurtin on 2005-12-24
that is how its supposed to be. its a security feature

that way some random virus or person cant go into synaptic and download stuff, or install things

---

### Post by mayankgarg1 on 2005-12-24
[QUOTE=briancurtin]that is how its supposed to be. its a security feature

that way some random virus or person cant go into synaptic and download stuff, or install things[/QUOTE]
But how I get the application run
After giving password system gets silent and no application is started.

---

### Post by Sutekh on 2005-12-25
Please copy the output of ```
groups <username>
```
using the name of your user.

To have admin privileges that user must be in the **adm** group

---

### Post by mayankgarg1 on 2005-12-25
Thanks Sutekh
I couldnot run Synaptic,Users-admin, Disks-admin in "run as different user"
I have checked aptitude .ther synpatic is not showing in Installed packaes and uninstalled packages
How can I solve this problem

---

### Post by Sutekh on 2005-12-25
What happens when you try the groups command?

---

### Post by Sutekh on 2005-12-25
If you have any other users with sudo privileges, use their login and use the command
```
sudo adduser <username> adm
```
using the sudo password of the other user, and <username> the name of the user who needs admin privileges

OR

If you don't have a user with sudo privileges, use this link
[Ubuntu Guide - How to gain root user access without login?]("http://www.ubuntuguide.org/#gainrootwithoutlogin")
This will get you into a root terminal.

And then use the command (similar to above)
```
adduser <username> adm
```

---

### Post by mayankgarg1 on 2005-12-31
Hi Sutekh
I have add the user in Adm group by using th command Adduser <username> adm
But still synaptic ,disksadmin gives error meessage Child terminated with status 1 like message.
Please help

---

