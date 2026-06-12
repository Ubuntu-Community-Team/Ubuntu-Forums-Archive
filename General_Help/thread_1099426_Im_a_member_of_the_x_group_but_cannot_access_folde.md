---
title: "Im a member of the x group but cannot access folder belonging to x group"
date: 2009-03-18
forum: General Help
---

### Post by redline99 on 2009-03-18
Hi, 

I created a folder called svn for my repository under /, then I created a group called svn with some members and changed the owner of the /svn folder with sudo chown root:svn /svn

So I checked /etc/group and svn group is there with 3 members in it including myself. 

I checked the /svn folder with ls -l and everything is good. 

I did all this but still cannot access the folder in any way unless I change the owner to my account instead of root. (I changed the permission of the folder to 770 btw) 

I just want to be able to create repositories with svnadmin under the folder /svn but can't unless im root. 

Any help greatly appreciated.

---

### Post by heindsight on 2009-03-18
New group memberships usually don't take effect until you log out and back in again. Have you tried that?

---

### Post by redline99 on 2009-03-18
no!!!! :mad:

and yes i feel bad about myself now, i spent more than an hour or two trying to figure it out... 

thanks it's working now...

This should be in the file/folder permissions page for ubuntu docs if it's not already there. Maybe I missed it.

---

