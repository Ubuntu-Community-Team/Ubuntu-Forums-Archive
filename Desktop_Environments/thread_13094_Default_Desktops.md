---
title: "Default Desktops"
date: 2005-01-28
forum: Desktop Environments
---

### Post by oracledarren on 2005-01-28
Hi

is there are way to create a duplicate version of a desktop for somebody else to use when they log in please ?

The scenario is this I log in as root to do all of my main admin work just to make things easier, but it would be useful that all of the apps and settings that I configured on roots desktop could be copies into another user name as well.

Just wondered if it is possible and if so what is the best way to achieve what I am looking for ?

Thanks

Darren

---

### Post by kosmic on 2005-01-28
Hi, to duplicate home directories for new users in linux, just put the files you want to show in the users home directories in :

/etc/skel



put everything you want to show in the new users homes in that directory and then it will show up whenever you create a new user.



sorry for my bad english

---

