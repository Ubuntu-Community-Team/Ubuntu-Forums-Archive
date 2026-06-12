---
title: "installing beryl error"
date: 2007-03-11
forum: Desktop Environments
---

### Post by kaboom on 2007-03-11
hey all i'm installing beryl on a dapper box with a radeon mobility 7500 video card.  i'm following this howto:   [http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html](http://lhansen.blogspot.com/2006/10/beryl-and-xgl-on-ubuntu-linux-with-ati.html)

with this step:  
kaboom@kaboom-laptop:~$ sudo apt-get install xserver-xgl  libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald-th emes beryl-settings xorg-driver-fglrx linux-restricted-m odules-`uname -r`

i'm getting this output: 
Reading package lists... Done
Building dependency tree... Done
xserver-xorg is already the newest version.
Some packages could not be installed. This may mean that  you have
requested an impossible situation or if you are using th e unstable
distribution that some required packages have not yet be en created
or been moved out of Incoming.
The following information may help to resolve the situat ion:

The following packages have unmet dependencies:
  beryl: Depends: beryl-core but it is not going to be i nstalled
         Depends: libberylsettings0 but it is not going to be installed
         Depends: libberyldecoration0 but it is not goin g to be installed
         Depends: beryl-plugins but it is not going to b e installed
         Depends: beryl-manager but it is not going to b e installed
  beryl-settings: Depends: beryl-plugins (>= 0.1) but it  is not going to be installed
                  Depends: beryl-settings-bindings but i t is not going to be installed
  emerald-themes: Depends: emerald (>= 0.1) but it is no t going to be installed
  xserver-xgl: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubun tu20.4 is to be installed
E: Broken packages

any ideas?
thanks 
chris

---

### Post by Kobalt on 2007-03-11
It says you have broken packages : open up Synaptic and go to Edit > Repair broken packages. 
Then you can try again to install your packages normally...

---

### Post by kaboom on 2007-03-12
hey thanks for the reply.  i fixed broked packages in synaptic then had the same problem in the terminal.  
thanks
chris

---

### Post by nikdc5 on 2007-03-16
I am also having this problem.

---

### Post by jhenager on 2007-03-16
Try looking at post #26 in this thread:
[http://ubuntuforums.org/showthread.php?t=268036&page=3&highlight=xgl+beryl+djrobbief](http://ubuntuforums.org/showthread.php?t=268036&page=3&highlight=xgl+beryl+djrobbief)

---

