---
title: "apt-get out of date? no tilda repositories ?"
date: 2006-08-05
forum: Desktop Environments
---

### Post by meph on 2006-08-05
i just installed a fresh copy of Ubuntu on my laptop since my server has been so nice to me and it's kicking me in the rear. what am i getting wrong.

i did 

sudo apt-get update 

and it did it's thing


> alex@laptop:~$ sudo apt-get install tilda
Reading package lists... Done
Building dependency tree... Done
Package tilda is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tilda has no installation candidate



> alex@laptop:~$ sudo apt-get install wine
Password:
Reading package lists... Done
Building dependency tree... Done
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

Some one please help me.

---

### Post by Jagot on 2006-08-05
Tilda and Wine are in the universe repository which you need to enable first.  See either of these links

[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by meph on 2006-08-05
thank you so much. 
you guys make me be thankfull that i switched to linux... 
one box running winblows left... in the house.. 

That worked. I remember doing something similar to that last time.
i need to learn how to use the 
.configure 
make 
make install 

deal

---

### Post by Jagot on 2006-08-05
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

---

