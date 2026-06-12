---
title: "setting environment variable"
date: 2005-06-08
forum: Desktop Environments
---

### Post by jeremytaylor on 2005-06-08
Hi there,
trying to get the intel compilers to work on my system, mostly sucessful but I need a way of setting the LD_LIBRARY_PATH variable so it doesn't keep on dissapearing. Any suggestions?
thanks
Jeremy

---

### Post by Alexander Kirillov on 2005-06-08
[QUOTE=jeremytaylor]Hi there,
trying to get the intel compilers to work on my system, mostly sucessful but I need a way of setting the LD_LIBRARY_PATH variable so it doesn't keep on dissapearing. Any suggestions?
thanks
Jeremy[/QUOTE]
 put it into /etc/bash.bashrc

---

### Post by alastair on 2005-06-08
Every the you launch a bash shell, BASH reads ~/.bashrc.

So, if it is just for you, add something like :

export LD_LIBRARY_PATH=<PATH>

to ~/.bashrc (i.e. /home/<your username>/.bashrc)

Then check via :

env|grep LD

perhaps.

---

