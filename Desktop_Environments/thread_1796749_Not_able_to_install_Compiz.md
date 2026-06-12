---
title: "Not able to install Compiz"
date: 2011-07-04
forum: Desktop Environments
---

### Post by FahadMKS on 2011-07-04
Hi,

I am using the Ubuntu 11.04 and I like to use the classic version rather than the Unity.
The problem is that, when I try to install the Compiz Simple settings, I get the message as not able to install.
Please help me to get the repository.
I have attached an screen shot.

---

### Post by 3Miro on 2011-07-04
Have you tried reloading the package list. Click reload and then try again.

---

### Post by steinerd on 2011-07-04
OK.. Not quite sure why it does not work for you or what may have happened to your repo's.  The Compiz config manager I used installed with this command.

```
sudo apt-get update && sudo apt-get install compizconfig-settings-manager
```

I hope that helps out some.

you can also go to the software manager and ensure that you have compiz and all of it's dependencies installed.  make sure you have the multiverse repos enabled also.

---

### Post by wildmanne39 on 2011-07-04
Hi, I would install the ccsm it shows it is required, and I would not install the simple ccsm at all it does not have as many options, also if you are going to setup the cube or effects you should know that you will need to revert compiz to the previous version because it lags in classic mode bad, I have a link for that and for setting up the cube in natty.
[http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html](http://www.webupd8.org/2011/05/how-to-downgrade-to-compiz-086-in.html)
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by FahadMKS on 2011-07-05
> **3Miro said:**
> Have you tried reloading the package list. Click reload and then try again. I have already tried that.

---

### Post by wojox on 2011-07-05
If you want to use the classic version just choose that session at login. :P

---

### Post by FahadMKS on 2011-07-06
That was indeed a great help wildemann39.........
Thanks to you and all others.

---

