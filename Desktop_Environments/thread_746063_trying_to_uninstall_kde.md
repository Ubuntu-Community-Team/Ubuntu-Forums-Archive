---
title: "trying to uninstall kde"
date: 2008-04-05
forum: Desktop Environments
---

### Post by slickh20 on 2008-04-05
I was checking out kubuntu a while back and didnt like it much but thought i would go back to it and check it out a few times i did and now i dont want it. so i uninstalled it with the sudo apt get uninstall kde stuff i was told to do and i did the oure gnome thing from psycho cats... but when i log on it still come on to the kubuntu splash screen and the kubuntu log in and i have still got a few kubuntu programs in here that i dont want.  is there somethin i am missing or do i need to just uninstall all of the stuff from add/remove and anything else in synaptic?

will this get my "turn off computer" button back in the quit menu instead of having to log out of user and then turn off?

thanks for any help

c

ok so i tried ununstalling just a couple packages form add/remove and i got this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

??

did i break it?

---

### Post by kellemes on 2008-04-05
> **slickh20 said:**
> I was checking out kubuntu a while back and didnt like it much but thought i would go back to it and check it out a few times i did and now i dont want it. so i uninstalled it with the sudo apt get uninstall kde stuff i was told to do and i did the oure gnome thing from psycho cats... but when i log on it still come on to the kubuntu splash screen and the kubuntu log in and i have still got a few kubuntu programs in here that i dont want.  is there somethin i am missing or do i need to just uninstall all of the stuff from add/remove and anything else in synaptic?

will this get my "turn off computer" button back in the quit menu instead of having to log out of user and then turn off?

thanks for any help

c

ok so i tried ununstalling just a couple packages form add/remove and i got this

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

??

did i break it?

I don't know how to remove the Kubuntu related stuff from your system but the last error message tells you to open a terminal window and type..
```
sudo dpkg --configure -a
```

---

### Post by slickh20 on 2008-04-06
```
casey@desktop2:~$ sudo dpkg --configure -a
[sudo] password for casey:
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
casey@desktop2:~$
``` 



ok i did 
and now i dont know what it did so now what? 

Thanks

---

### Post by benerivo on 2008-04-06
There are two things you need to do. One is to reinstate the gnome login manager, and the other is to wipe the other kde packages you have left on your system. I would do ```
sudo dpkg-reconfigure gdm
``` from a terminal, then i would restart to make sure it uses gdm. Then i would use synaptic and search for "kde" and delete the packages it finds, being very careful that each one i choose to remove doesn't also remove packages i want to keep (err on the side of caution).

---

