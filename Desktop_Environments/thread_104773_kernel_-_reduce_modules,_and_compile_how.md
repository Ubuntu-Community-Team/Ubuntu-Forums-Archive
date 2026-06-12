---
title: "kernel - reduce modules, and compile how?"
date: 2005-12-16
forum: Desktop Environments
---

### Post by dartakaum on 2005-12-16
Hy, i want to take some modules from kernel that i'm not using, so, how can i do that? 

another problem if source is needed how do i download another one? cause i deleted /usr/src/linux-kernel-2.6.12 and other sources from there, and if i do apt-get linux-source it says i already got it... :\

---

### Post by Sutekh on 2005-12-21
[QUOTE=dartakaum]Hy, i want to take some modules from kernel that i'm not using, so, how can i do that? [/QUOTE]
If they're modules then you should be able to remove them with the command
```
rmmod
```
[man page for rmmod]("http://linuxcommand.org/man_pages/rmmod8.html")

Ed: it seems that using
```
modprobe -r
```
is the better option. [man page for modprobe]("http://linuxcommand.org/man_pages/modprobe8.html")

[QUOTE=dartakaum]
another problem if source is needed how do i download another one? cause i deleted /usr/src/linux-kernel-2.6.12 and other sources from there, and if i do apt-get linux-source it says i already got it... :\[/QUOTE]
Did you delete it yourself?  

Use apt-get or Synaptic to remove it. I know it's not there, but maybe apt-get will feel better if it 'removes' it first.  Then try to re-install it.

---

