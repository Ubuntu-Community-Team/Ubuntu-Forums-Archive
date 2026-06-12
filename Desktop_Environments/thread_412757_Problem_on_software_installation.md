---
title: "Problem on software installation"
date: 2007-04-18
forum: Desktop Environments
---

### Post by tvgyg on 2007-04-18
I was trying to install the software from CDROM on Ubuntu 6.1. 
But I always got the following error message after running the installation script (:~$ /media/cdrom/install):

/bin/csh: bad interpreter: Permission denied


Many thanks ahead.

---

### Post by newtonfn on 2007-04-18
Apparently your program is trying to run a shell that it is not installed on ubuntu.
You can try to get the csh shell form the repositories writting at a console:

```
sudo apt-get install csh
```

And then try to install your program.
Good luck

---

### Post by tvgyg on 2007-04-19
Thanks for helping. 

The installation script still doesn't work in CSH shell,  But this time it only says:

Permission denied

Same result when I ran it as root.

Any ideas?

---

