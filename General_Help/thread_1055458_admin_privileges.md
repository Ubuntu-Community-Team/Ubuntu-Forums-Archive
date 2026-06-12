---
title: "admin privileges"
date: 2009-01-30
forum: General Help
---

### Post by hockey9876 on 2009-01-30
When I installed ubuntu, I made myself an administrator of the
system.  Now, for some reason, I'm unable to do any administrative
functions.  According to /etc/group, I'm in the admin group,
so I don't understand why I'm unable to perform these functions.
One of the errors I see when trying sudo functions is:

must be setuid root

I found the following and looked  which has already been discussed, 
[http://ubuntuforums.org/showthread.php?t=219767](http://ubuntuforums.org/showthread.php?t=219767)
but none of the suggestions have helped.

Can anyone suggest anything, short of reinstalling the os?

Thanks,

John

---

### Post by gettinoriginal on 2009-01-30
No need to reinstall, most everything can be fixed.  Try this in terminal:
```
gksudo adduser **your_user_name** admin
```

---

### Post by gettinoriginal on 2009-01-30
Just for information, if you ever do a fresh install again, sudo is just a command allowing access to root, and is controlled by the password of the installing user.  There is no need to install as root.  :p

---

