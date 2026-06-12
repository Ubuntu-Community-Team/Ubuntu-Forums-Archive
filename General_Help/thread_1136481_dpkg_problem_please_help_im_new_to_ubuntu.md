---
title: "dpkg problem please help im new to ubuntu"
date: 2009-04-25
forum: General Help
---

### Post by CrazyPenguin03 on 2009-04-25
Hey. Eh ok so I have read through a lot of threads already so I'm going to post my own because none of the advise works. Any how I have a dpkg problem where it tells me

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

and then I run termail and do what it says even using sudo and it tells me

crazypenguin@crazypenguin-laptop:~$ sudo dpkg --configure -a
dpkg: error processing hal-info (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Setting up ubuntu-docs (8.06.1) ...

Setting up libc6 (2.7-10ubuntu4) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 hal-info

so does anyone know why my machine is messing up? Do I need to reinstall Ubuntu or is there a way to recover my system?

---

### Post by lisati on 2009-04-25
You might want to try the following: ```
sudo aptitude reinstall hal-info
```

---

### Post by malachi1990 on 2009-04-25
Which version of ubuntu are you using? 8.04, 8.10, 9.04? 

Depending on your version of ubuntu, and your problem, you can fix this by typing this into your terminal:

sudo apt-get update 

(Please post any error output from this)

And then:

sudo apt-get upgrade

(Again, please post any error output from this)

If this doesn't work, go to System > Administration > Software Sources.  From here, go to the input box beside "Download from" and change the server from which you download.  

Hope this helps.

---

### Post by CrazyPenguin03 on 2009-04-25
well malachi1990 your advise seems to be working. no errors yet. but it says it well take close to two hours so I will reply with any errors then. Thank you guys so much ^^

---

