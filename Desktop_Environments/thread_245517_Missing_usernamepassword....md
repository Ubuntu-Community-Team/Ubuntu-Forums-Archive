---
title: "Missing username/password..."
date: 2006-08-27
forum: Desktop Environments
---

### Post by gironja on 2006-08-27
Hi!

I've installed Ubuntu Alternate to a friend's PC. I've also used the oem-config utility before give it to him, so that he can enter all his info himself. But when he tries to log on with his username and password, it gives an error that the username or password is incorrect. I know he used a "long" username (more than 8 characters), with lower- and upper-case, and I think he might use a period inside. Is there any way to find or retrieve the correct username that the PC registered and/or his password? 

Thanks for the help on this issue.


jNa

---

### Post by aysiu on 2006-08-27
Have you tried booting into recovery mode and then typing this? ```
cd /home
ls
``` That should show you the users on your system.

---

### Post by gironja on 2006-08-28
Really I haven't try anything yet, since I'm away from home, but I tried to do some things in my PC as if it were his', but I always get a login screen, which will not let do anything until the users logs-on. So, I think it won't work, but I'll double-chek today, and   post any news...

Thanks!

---

### Post by gironja on 2006-08-30
It was true: I don't need a password in recovery mode.  But there is another issue: typing "ls" at "/home" does not give me anything.  So, there is no user account.  I tried to create one using "useradd" (I think that one is the command), but it appears to make it, but there is still nothing at "/home".  Is there anyway to create an user account from recovery mode? :confused:  
Before deliver the PC to its owner, I ran "oem-config-prepare" (I was using the 6.06 Alternate version).  Is there anyway to use "oem-config-prepare" again (since the command is not found)?  

Thanks for all your help!:D

---

### Post by aysiu on 2006-08-30
Not sure if this'll make a difference, but have you tried *adduser* instead of *useradd*? ```
adduser gironja
adduser gironja admin
reboot
```

---

### Post by gironja on 2006-09-03
Sorry for the delay.

Well, I haven't try that; I didn't knew it exists, LOL. Anyways, I'll try that in the machine (in a phone-support call) and I'll tell you the results. I hope I'll do that today, to have an answer as soon as possible. Thanks!


jNa

---

### Post by gironja on 2006-09-03
Finally the PC is working!!!

Thanks for your help AYSIU!! I've done exactly what you said, and now it is working as it should.

Thanks!


jNa

---

