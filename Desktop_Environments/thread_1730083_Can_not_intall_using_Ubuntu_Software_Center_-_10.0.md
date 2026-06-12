---
title: "Can not intall using Ubuntu Software Center - 10.04"
date: 2011-04-15
forum: Desktop Environments
---

### Post by wshore on 2011-04-15
A few weeks ago I jumped into Ubuntu by installing 10.04 on an old PC. All was working fine until today. I have been trying things all do to fix this.

When I try to install from the software center, nothing happens. Nothing!  It worked fine before. I did an update early today. I have even updated one new update late today. But the software center will not install anything. The install button goes grey for about a second, then back to normal.

I went to System, Administration, Software Sources, Other Sources (tab), clicked partner - to rebuild the package info. That did not change anything.

I am not sure how to update to 10.10 since I am new to Linux.

Help.

---

### Post by wshore on 2011-04-15
OK...
so if I run sudo software-center, it works.

It must be related to my only single login not getting prompted for a password for root. Maybe?

I had tried to create another user today, but it failed. I can not create a new user. So what do I need to look for???

---

### Post by wshore on 2011-04-15
Ok....
I can change and add users with sudo users-admin.

I checked and I have full admin set for me.

Still no way to install from the software center or add users without doing a sudo <command>.

What am I missing?

---

### Post by Krytarik on 2011-04-15
Try reinstalling the package "gksu":
```
sudo apt-get install --reinstall gksu
```
Greetings.

---

### Post by wshore on 2011-04-16
That did not work.
It seems that only the one user is effected by this issue.
Not sure why. I had to create a new user with command line interface and the new user is fine.

---

