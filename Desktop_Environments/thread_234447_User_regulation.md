---
title: "User regulation"
date: 2006-08-11
forum: Desktop Environments
---

### Post by lemonsCC on 2006-08-11
I have several questions about users while i wait for my box to compress 9gb.  :p 

1) is it possible to force a user to logout?  (using root, sudo, etc)
--One of our computer users leaves his user logged in running several online games running, which really bogs down our system

2) is it possible to only allow a user to be on the computer for a certain number of minutes/hours per day?

3)when setting up this box I would like all the users (except 1) to be identical (appearence, permissions, plugins, etc)  is it possible to do this?

---

### Post by jordilin on 2006-08-11
1- Yes, do 
```
who -u
```
in the right part you'll get the pid number of the shell the guy is using,
then kill it
```
kill -9 pid
```

2- Yes, try timeoutd
I've never used it, but I'm sure there are plenty of tutorials out there.

3- Yes, just copy the home directory of one user (for instance doing rsync) and transfer it to the home of the other user. You can use partimage as well to make exact partitions of the home directory.

---

### Post by lemonsCC on 2006-08-11
2) timeoutd never worked for me before.  is it more compatible with dapper?


3)  these options will "clone" the user?  if so thank you a million, so many hours saved!

---

### Post by jordilin on 2006-08-11
> **lemonsCC said:**
> 2) timeoutd never worked for me before.  is it more compatible with dapper?


3)  these options will "clone" the user?  if so thank you a million, so many hours saved!

2) I've never tried timeoutd, so I can't tell you. But Ubuntu is Debian based, so I'm pretty sure it will work. 

3) Having an exact copy of the /home/username partition and copying to the other users you'll have all users with the same preferences, plugins, etc...

---

