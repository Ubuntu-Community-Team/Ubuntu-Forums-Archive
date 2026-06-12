---
title: "setfacl help"
date: 2011-04-21
forum: Desktop Environments
---

### Post by lucacerone on 2011-04-21
Dear all,
I'd like to have a directory accessible only by 3 specific user and
no-others.

Say the user are called u1 u2  and that u1 is the one creating the directory project. I also would like that whenever one of the two users creates a file the other is able to modify it. Also I would like that subfolders would have the same permission as the parent one.
(I know I could create a group with only u1 and u2, but I'm really trying to understand how to use setfacl and getfacl)

I (u1) try to configure the directory as follows:

mkdir project
chmod go-rwx # so that I remove the permission to everyone who is not u1.
chmod u+s project
setfacl -R -m d:u:u1:rwx,d:u:u2:rwx,u:u1:rwx,u:u2:rwx,m:u1:rwx,m:u2:rwx,d:g::---,d:o::---,g::---,o::--- project
The command doesn't work, but I can't understand why.
Can someone help me figure it out how to use setfacl properly
and how to set the right permissions so that I can get the protection that I want?
Cheers, -Luca

---

