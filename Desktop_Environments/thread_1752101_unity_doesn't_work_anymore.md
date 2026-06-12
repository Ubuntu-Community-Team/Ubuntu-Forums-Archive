---
title: "unity doesn't work anymore"
date: 2011-05-07
forum: Desktop Environments
---

### Post by razorbackfan on 2011-05-07
I have recently updated to natty narwhal and was running it fine with the unity desktop for almost two weeks. Then when I boot up ubuntu today I get a notification that I do not have the required hardware to run unity. I  have a brand new hp dv7 4100 not sure exactly what my other hardware is. How do I fix this?

---

### Post by Krytarik on 2011-05-08
Try adding "UNITY_FORCE_START=1" to "/etc/environment".

Greetings.

---

### Post by razorbackfan on 2011-05-09
[INDENT]When I input the command /etc/environment I get the the response Permission denied. I am the administrator so I don't know why it would say that. When I looked in the file system I didn't find a folder for environment. I'm a linux noob so you may have to eplain it a little bit please. Thanks for the help
[/INDENT]

---

### Post by 3ar1 on 2011-05-10
> **razorbackfan said:**
> [INDENT]When I input the command /etc/environment I get the the response Permission denied. I am the administrator so I don't know why it would say that. When I looked in the file system I didn't find a folder for environment. I'm a linux noob so you may have to eplain it a little bit please. Thanks for the help
[/INDENT]

/etc/environment is a text file not a command. You need to edit it with, e.g. gedit. Try:

sudo gedit /etc/environment

(sudo gives you super user privileges).

---

### Post by Krytarik on 2011-05-10
Yeah, besides the fact that you should use 'gksu'/'gksudo' instead of 'sudo' to prevent possible serious issues when you run graphical apps as root, *3ar1* is absolutely correct.

See here on how to gain root access on the command line and for graphical apps:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

