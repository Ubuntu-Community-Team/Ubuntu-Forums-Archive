---
title: "Edubuntu User Permissions"
date: 2007-08-19
forum: Desktop Environments
---

### Post by nroussi on 2007-08-19
I have just installed an edubuntu server 7.04 with a few thin clients and a few users, Everything is working fine except the user permissions. 
For example, I created the user john as the first account during installation. Then after the thin client setup and everything, I created users mary, andy and mark. I did not select that these new users should be able to administer this computer. The new users (mary, andy and mark) are able to read the home directory and the documents in the home directory of john. I was under the impression that the home directory of every user is private to that specific user. I know I can chmod /home/john for only john but I was wondering if there is a way so that when a new user is created to not be able to view all the other home directories.

Thanks

---

### Post by aysiu on 2007-08-19
The default is actually to have users' home directories readable for other users but not writable by them.

[This](http://ubuntuforums.org/showpost.php?p=832721&amp%3bpostcount=9) may help you change the default permissions.

---

