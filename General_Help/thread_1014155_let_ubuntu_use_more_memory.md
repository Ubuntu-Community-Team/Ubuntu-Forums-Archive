---
title: "let ubuntu use more memory"
date: 2008-12-17
forum: General Help
---

### Post by oddish2211 on 2008-12-17
i know what you are all thinking, "why would you want to use more memory?"
i've currently 3 GB of ram in my laptop (1x1 1x2), but ubuntu only uses ~ 1 GB max when i'm playing WoW in Wine. and when i'm doing other things, ubuntu still uses only 1 GB, of course this is great but i want to use the remaining 2 GB because it remains unused when i'm working/playing on my pc. maybe for preloading other programs like firefox?
or using less swap space?

how can i use this remaining space for like speeding up ubuntu?

---

### Post by Existentialist on 2008-12-19
Some people say that they notice performance differences when changing the "swappiness" in Ubuntu.  This can reduce the amount of data the system pages and allow it to use your RAM instead.

>sudo gedit /etc/sysctl.conf

There is a line 

vm.swappiness=##

The lower you set that value, the less swap space should be used.  I wouldn't recommend going below 10 initially.  Try out different values to ensure stability and see what kind of difference you get.  Note that it will not take effect until rebooting after saving your changes.

---

### Post by sdennie on 2008-12-19
The linux kernel already does what you are asking for actually.  Run the command "free -m".  You will see that Ubuntu is using much if not most of your RAM for cache and buffers.  You can also force this behavior to be a bit more predictable using the preload deamon:

```

sudo apt-get install preload

```

It should be running after that and the config can be found in /etc/preload.conf.

---

