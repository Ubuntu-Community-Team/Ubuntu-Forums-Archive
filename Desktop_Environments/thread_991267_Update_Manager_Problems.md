---
title: "Update Manager Problems"
date: 2008-11-23
forum: Desktop Environments
---

### Post by DucksAndDolphins on 2008-11-23
I am fairly new to Ubuntu, and ever since day one I've had a number of updates that needed to be initiated, however, every time I attempted to install them, I received an error message reading:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Naturally, I ran dpkg --configure -a through my Terminal. It then told me that a "superuser privilege" is required for me to be able to run said command.

Help?

---

### Post by ajgreeny on 2008-11-23
```
sudo dpkg --configure -a
``` will do it.  Ubuntu doesn't use a root account, but uses ```
sudo command
``` instead.  See [*Root sudo*]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Swagman on 2008-11-23
> **DucksAndDolphins said:**
> I am fairly new to Ubuntu, and ever since day one I've had a number of updates that needed to be initiated, however, every time I attempted to install them, I received an error message reading:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Naturally, I ran dpkg --configure -a through my Terminal. It then told me that a "superuser privilege" is required for me to be able to run said command.

Help?

Do what it's telling you literally.

In other words... Open a terminal

Applications > Accessories >Terminal

and type

```
sudo dpkg --configure -a
```

press enter
It will ask you for your password ..Yes the one you login with

Press Enter

Thats it.

---

