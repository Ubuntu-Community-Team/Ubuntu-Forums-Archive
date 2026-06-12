---
title: "[SOLVED] logout/turn off/restart is waiting for something"
date: 2008-04-10
forum: Desktop Environments
---

### Post by DarK SouL on 2008-04-10
I have been looking around for a few days for a solution on this and haven't found any, so here is my port.

I am fairly new to ubuntu, but the last time I used a linux system was in the 56k days so please bare with me :).

Here's the problem, whenever I try to logout or restart the system it keeps waiting for something, when i am able to activate the shell window pressing ctrl + alt +  F8 the last [OK] is at rm.local, if I press the power button it will force everything to close and the next program to close would always be gdm, so I assume thats the one causing the wait.

I created another account to see if it had the same problem but I was able to logout/restart/shutdown without problems with it, so I am guessing there is something on my main account causing this, where could I begin to look?

---

### Post by warp99 on 2008-04-10
Here's a little tip. If you delete the hidden directories and files within your share then press ctrl+alt+backspace when you login again they will be recreated with default settings just like the first time you booted into Ubuntu. 

The only files that need to be there are: 
```

~/.bashrc 
~/.bash_logout 
~/.bash_profile
~/.profile
```
the rest can be removed and they will be recreated on login.

---

### Post by DarK SouL on 2008-04-10
Awesome! that worked!

Thanks a lot!

---

