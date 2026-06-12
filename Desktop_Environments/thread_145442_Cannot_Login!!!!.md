---
title: "Cannot Login!!!!"
date: 2006-03-16
forum: Desktop Environments
---

### Post by Naresh_4 on 2006-03-16
my problems have just gone from bad to worse, i have no idea what happened. it started off being what i had thought to be minor problems:  

[http://www.ubuntuforums.org/showthread.php?t=145415]("http://www.ubuntuforums.org/showthread.php?t=145415")

to not being able to login. when i try to, i get this mesage:

"Your $HOME /.dmrc file has incorrect permissions and is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions."

however, the failsafe logins are atleast working. can someone please help?

---

### Post by 4dz0 on 2006-03-16
in the failsafe terminal try:

sudo chown username $HOME/.dmrc

where username = your login user name

and aslo:

sudo chmod 644 $HOME/.dmrc

---

### Post by taurus on 2006-03-16
Since there is something wrong with your ~/.dmrc so why don't you change the permission (or owner) back so you can log into your account again.  Boot into safe mode and run these at the terminal
```

cd ~jack
chown jack .dmrc
chmod 744 .dmrc

```
assuming that "jack" is your login name.  Substitude the right one for it...

---

### Post by Naresh_4 on 2006-03-17
I tried to do the stuff that u said. i still cant login, and am still getting the same error.

---

### Post by Naresh_4 on 2006-03-17
actually its ok now, i did a forum search and found out the solution, for those of you with the same problem, just search "permissions 644" and ull get ur answer :) 

thanks alot for the help

---

