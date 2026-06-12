---
title: "wont allow theme"
date: 2007-11-18
forum: Desktop Environments
---

### Post by darksora145 on 2007-11-18
You must be the root user to configure GDM what does that mean? when i tried to GDMsetup it showed that

---

### Post by puccaso on 2007-11-18
something that i dont understand why it hasnt been done already but..

goto terminal

su
type password, 
nano -w /etc/group
find the group adm and admin, add your user name there,
ctrl+o to save
then ctrl+x to exit..
log out, log in.. 

now you will be able to admin your system as you need too.. 
hope it helps.

---

### Post by darksora145 on 2007-11-18
uhh you lost me on find the group adm and admin, add your user name there, I found the admin but not group adm. Is it called "root"?

---

