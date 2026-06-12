---
title: "Ubuntu totally messed up by beryl (and myself)! Help Needed"
date: 2007-02-13
forum: Desktop Environments
---

### Post by kramer65 on 2007-02-13
Hello,

I tried to install beryl (because it looks sooo beautiful..:-)). I tried several things (using [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX) and installing/command line stuff/messing with /etc/X11/xorg.conf etc) but it seemed that my Ati Radeon 9800 was not installed properly. So I downloaded the drivers from [http://ati.de/support/driver.html](http://ati.de/support/driver.html) . After logging in as root (found at [http://ubuntuforums.org/archive/index.php/t-31053.html](http://ubuntuforums.org/archive/index.php/t-31053.html)) I installed it. This was the big blow to my system, and now when I start up Ubuntu, I first get the whole login-bar-thing with all the ok's, after which it ends in a total system error Saying:

"Failed to start the X-server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

Clicking yes gives me this:

"X Window System Version 7.0.0
Release Date: 21 Dec 2005
X protocol Version 11, Revision 0, Release 7.0
Build operating system: Linux 2.6.15.7 i686
Current Operating system: Linux ricom 2.6.15-28-386 #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007 i686
Build date:16 march 2006
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org) to make sure you have the latest version
Module loader present"

After which I can press ok after which I can use the command line.

I did backup the xorg.conf in the same folder. But would I be able to get it back via command line? Or wouldn't that matter? Did that driver do other stuff?

Can anybody help me out of this mess? I promiss I wil not do stupid stuff anymore..  :|

---

### Post by ghandi69_ on 2007-02-13
You might get flamed for posting a topic about beryl in absolute beginner talk, and for your limited vocabulary... :) 

I havent used berly much, but i've heard this command is useful for when xorg gets screw

sudo dpkg-reconfigure xserver-xorg

give it ago from the terminal... unless someone comes in here and tells you not to first.

---

### Post by shareMenaPeace on 2007-02-13
You can use the link in my sig to uninstall beryl.

---

### Post by annda on 2007-02-13
navigate to the directory where xorg.conf is stored
```
cd /etc/X11
```
then find out exactly what the backup file is called
```
ls -a
```
then overwrite the bad file with backup
```
sudo mv the_name_of_your_backup xorg.conf
```

---

### Post by bodhi.zazen on 2007-02-13
Well you certainly can try your old xorg.conf ...

After that, IMO the easiest way to install teh ATI driver is with envy ;

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

After that beryl :p

---

### Post by kramer65 on 2007-02-13
Alright!

Linux is working again (writing now from it.. :-))

Gonna give it another try with beryl! :-)

Thank you so much for the help! Without this community I would have given up ubuntu already! But with the always quick help of everybody here I can continue and hopefull get my friends enthousiastic for ubuntu as well to spread ubuntu. :D

---

