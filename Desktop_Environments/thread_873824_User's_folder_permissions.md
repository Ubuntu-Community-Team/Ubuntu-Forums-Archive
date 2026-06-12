---
title: "User's folder permissions"
date: 2008-07-29
forum: Desktop Environments
---

### Post by nir78 on 2008-07-29
Hello,

My computer is used by many users (local or via ftp).
I have noticed that when I create new user with group "users" he is able to view any file on the system.
My intention is to allow him to view only his home and another folder.
How can I do this? I noticed that for each folder I can define only one group while I want user A to not being able to execute any file in the folder and user B to be able to do anything in the folder... 
Is there a windows like possibility of connecting user to some group and define per folder behaviour for each group ?

Thanks in advance,
Nir

---

### Post by ilrudie on 2008-07-29
Look into acl (access control list) by typing man acl in a terminal.  I have not set them up but it is my understanding that they can accomplish what you are looking for and are part of Ubuntu by default.  You may need to turn them on if /etc/fstab for the partition you need them on but I think all the required packages are part of a standard install.

---

