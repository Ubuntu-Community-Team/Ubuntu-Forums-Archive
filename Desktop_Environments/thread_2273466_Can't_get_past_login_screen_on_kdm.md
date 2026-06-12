---
title: "Can't get past login screen on kdm"
date: 2015-04-13
forum: Desktop Environments
---

### Post by sagar7 on 2015-04-13
I installed kde-full and selected the wrong display manager during install. Now I get a completely different log in screen, and my credentials just don't work on it. How do I get back to the original lightdm?

I have tried Ctrl+Alt+F2, but this opens up a console which asks for the user name and password, but as I said above, my credentials simply don't work.I remember my user name being "Amit Limaye", which in Ubuntu is stored as amit, if I'm not mistaken, so I tried that, but it doesn't work.

Is there a way to get back to lightdm without a reinstall? Also, please give me the commands to set lightdm as the default. I would also appreciate if somebody gave me step by step instructions to view the user names, and to reset passwords on the accounts.

P.S. I'm a complete Linux noob, so go easy on me. :D Also, please remember that I CANNOT enter ANY commands on that kdm screen, because I can't login at the ttyl, so I need alternative solutions to that.

---

### Post by Vladlenin5000 on 2015-04-13
```
sudo dpkg-reconfigure lightdm
``` to get back the original.
However, your credentials are the same and always have been. You're typing it wrongly. Linux is case sensitive and yes, you must know your username as well as your password.

---

### Post by sagar7 on 2015-04-13
It has been a long time since I came back to Ubuntu, so I think I may have forgotten my user name, but I'm pretty sure I know the password. Is there a way I can check for user names?

---

### Post by sagar7 on 2015-04-14
I have logged in using the root account. Thanks.

---

### Post by dino99 on 2015-04-14
> **sagar7 said:**
> I have logged in using the root account. Thanks.

its very scary, stay safe with a user session. If your initial user name is forgotten, then simply create a new one.

---

### Post by Vladlenin5000 on 2015-04-14
First things first, Ubuntu doesn't use the root account approach. The root password is the same of the first user defined for the system and users are encouraged to use only *sudo* whenever privileges are required.
Secondly, if your **name** "Amit Limaye" then most likely your **username** is "amit" as per the usual naming convention the installer uses, but you can change it so... You and only you know what you did when installing. If you accepted the defaults then it should be "amit".
This is the one and only account you'll ever need to login with, graphically or in a console. Anything you need beyond a regular user do it with *sudo* so just login in the console with "amit", issue the commend I mentioned in the first reply, follow the instructions and you should have lightdm back in no time.

---

