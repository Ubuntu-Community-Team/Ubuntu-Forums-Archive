---
title: "Ubuntu 10.10 - How to get rid of boring motd ?"
date: 2011-03-28
forum: Desktop Environments
---

### Post by MalteseUnderdog on 2011-03-28
Hi there,

[On Ubuntu 10.10 64-bit] 

I have been trying to get rid of the boring motd when ssh-ing into the machine.  I have sudo vim-ed the /etc/motd file to no avail.

Even if I add a motd.tail tail file with my content.  I still get the boring and verbose:

> 
Linux barney 2.6.35-28-generic #49-Ubuntu SMP Tue Mar 1 14:39:03 UTC 2011 x86_64 GNU/Linux
Ubuntu 10.10

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)


As if someone will read the documentation ! :)

How do I get rid of this?

Thanks
JP

---

### Post by stinkeye on 2011-03-28
The scripts which generate the motd file are contained in **/etc/update-motd.d/**
See here [**_[COLOR="DarkRed"]http://ubuntuforums.org/showthread.php?p=10610310[/COLOR]_**]("http://ubuntuforums.org/showthread.php?p=10610310")

---

