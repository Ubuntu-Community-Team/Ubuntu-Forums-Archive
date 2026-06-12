---
title: "Up date manager"
date: 2009-01-01
forum: General Help
---

### Post by johnmd on 2009-01-01
A few days back I ran the update manager and during the update my computer froze.
I had to reboot it.
No when I try to run the update manager it searches and finds the newest updates and shows them but when I try to install them I get the following error.
When I go to a terminal I get a message saying that I have to be super user which I am.
I went to a terminal session for the screen that you select the users on and got now where on that one.
It kept telling me that i had to run an option.
I'm not even sure what I am trying to do.
Can anyone help.

John 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by drs305 on 2009-01-01
> **johnmd said:**
> 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


run this:
```
sudo dpkg --configure -a
```

You will have to enter your password, and you won't see it as you type.

---

