---
title: "&quot;Network path not found&quot; in Samba"
date: 2006-07-18
forum: Desktop Environments
---

### Post by Flyn on 2006-07-18
Here goes:
The Ubuntu server has two users, the user I'm currently using to run normal tasks and a user created for samba logins. The samba user can see the computer and can access his home directory, but if I try to access directories not in his home folder, I get the network path not found message. I'm guessing this has something to do with permissions, has anyone else encountered this before?

Thanks in advance,

---

### Post by Thund3rstruck on 2006-07-19
When you configure samba, you must specify the user (smbuser) permissions, the directories to share, etc.

Refer to [The Unofficial Samba Guide]("http://hr.uoregon.edu/davidrl/samba.html")

or 
$man samba

for assitistance

---

