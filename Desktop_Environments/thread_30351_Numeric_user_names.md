---
title: "Numeric user names"
date: 2005-04-28
forum: Desktop Environments
---

### Post by khansen46 on 2005-04-28
Is it possible to make Linux allow numeric user names?
I am a Desktop Support Specialist, and have been pushing to get Linux in our environment. I installed Ubuntu on a notebook yesterday, and was able to get Evolution working with our Exchange server in a matter of minutes (for the first time, after trying many distros). Ubuntu has been the easiest for me to set up, and has given me nearly every resource I need for my work environment. I have 2 challenges left, and I can make a push to start "officially" testing Ubuntu in our office. One is Gnomemeeting, which hangs up every time I try to configure it. (I'll address that later, though, as TightVNC could easily replace Net Meeting for remote control).
 The other issue is that our Network department has gone to using our employee numbers for network logons. In order to get Linux into our environment, we have to be able to log in using employee numbers. This is one area they won't budge on. They won't accept any "work arounds" or "fixes".
Anyone have any ideas?   ](*,)

---

### Post by TravisNewman on 2005-04-28
```

travis@Eniac:~$ sudo useradd 1234
travis@Eniac:~$ sudo passwd 1234
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
travis@Eniac:~$ su 1234
Password:
sh-3.00$

```
It seems to work ;)

---

### Post by lao_V on 2005-04-28
It seems like a very very bad idea/practice to have numerical only user logins, no?

---

### Post by khansen46 on 2005-04-28
It wasn't my choice...and some people can really be stuck on an idea. We fought the idea...unsuccessfully   :?

---

### Post by lao_V on 2005-04-28
I wasn't blaming you :-) Sometimes management can be so stuck up!! ](*,)

---

### Post by khansen46 on 2005-04-28
Looks like it worked. I have to do all user config from the command line, though. If I try to do anything in graphical, I get errors about an invalid user name. Inconvenient, but I'll try to work around it. Any ideas where a main config file may be where I can get rid of this restriction altogether?

---

