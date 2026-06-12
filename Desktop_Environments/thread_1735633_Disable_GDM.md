---
title: "Disable GDM"
date: 2011-04-21
forum: Desktop Environments
---

### Post by bring1 on 2011-04-21
Greetings,

I'm working on an ubuntu 10.04.2 desktop I set up on my girlfriend's laptop back home, unfortunately, I'm on business and it's 4000 miles away and I only have SSH and VNC access to it.

I'm using it as a server, and the GDM is really sucking away resources, so I'd like to know if I can disable GDM in favor of just the command line while keeping the wireless settings I've already set up (using network-manager, I believe). It would be really bad if I screwed it up and wasn't' able to automatically connect to the wireless network. 

Thanks!

---

### Post by Krytarik on 2011-04-21
Please see here on how to boot into "text" mode, without GDM:
[http://ubuntuforums.org/showthread.php?p=9644518#post9644518](http://ubuntuforums.org/showthread.php?p=9644518#post9644518)

Of course, you need to run "startx" to get an Xsession then, and I do believe that at least after doing so you have exact the same network available like with GDM.

But I do not know, if your network would also be available at the command line, since some configs apparently need the Network Manager.

Hope it helps!

---

### Post by bring1 on 2011-04-22
Thanks! Totally and completely worked (I opted to add a text menu entry and set as default). Network-manager stayed alive.

---

### Post by sisco311 on 2011-04-22
Cool! Don't forget to mark this thread as solved.

Oh, and welcome to the forums!

---

