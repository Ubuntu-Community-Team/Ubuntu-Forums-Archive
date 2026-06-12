---
title: "Permission issues"
date: 2009-01-05
forum: General Help
---

### Post by sheishkabob on 2009-01-05
I'm trying to copy some file between multiple users, and it doesn't go my way. I tried to google the issue and it appears everyone is stuck with what i want. Everyone is asking to keep permissions when copying, I want them to change. When I copy a file from userA's home to userB's home, I want userB to have full control. When I copy it however, userA remains the owner and userB can't do anything with it. 

Does anyone know of a way to fix this?

---

### Post by alan34 on 2009-01-06
To give userB ownership of the fileA - in a terminal go

sudo chown userB fileA

To give userB ownership of *all* files and directories under directoryA

sudo chown -R userB /pathto/directoryA

info chown gives a full list of options.

You could also add userB to userA group and viceversa like

gksudo gedit /etc/group

find the line with userA and add userB - userC etc

userA:x:somenumber:userB,userC

Here is mine

alan:x:1000:tom,dick,harry

ls -lisa

gives you all the ownership - groups and rwx permissions.

I would also look at 

info chmod

Hope this is some help

---

### Post by The Cog on 2009-01-06
If you copy the file to /tmp then every user can access the file and take a copy it for themselves. Then you just need to delete the temporary copy when they've all got their own copy.

---

### Post by sheishkabob on 2009-01-15
thanks, and sorry it took so long to say so.

---

