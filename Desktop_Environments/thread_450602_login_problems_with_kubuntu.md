---
title: "login problems with kubuntu"
date: 2007-05-21
forum: Desktop Environments
---

### Post by ronmaroria on 2007-05-21
Just installed my Ubuntu last night and was using it without any problems. Then while adding some customizations, i installed automatix2, i also got the Kde desktop and made it my default desktop, then shutdown and went to bed. on waking up this morning, Kubuntu login comes up, i put in my user name and password, it goes black for a little bit and the login screen comes back again. It happens repeatedly. When i put in wrong login info on purpose, it tells "login failed", as expected though. what seems to be the problem.

---

### Post by taurus on 2007-05-21
See if you can log in from a console, <Ctrl><Alt>F2.  Then post the output of this command.

```
df -h
```
Any reason why you decided to install Automatix2 on your machine?  Feisty should come with anything that you need in Applications -> Add/Remove.

---

### Post by kannedheat on 2007-06-02
I have the same problem.

---

### Post by gufuchs on 2007-06-02
Same Problem here, too. (running kubuntu 6.06.1)
only 10% of the disk is used.
/var/log/Xorg.0.log shows no critical errors.
~/xsession-errors show something like
"No profile for user 'myusername' found"

But I haven't found out which profile is meant.

---

### Post by harperd on 2007-06-29
I discovered I had the same problem today - do we have a resolution?

---

### Post by jpmswiss on 2007-08-23
Uh-oh....I got the same problem!

Suddenly unable to login......only via Terminal but no interface.

StartX doesn't go either !

Help pls!

---

