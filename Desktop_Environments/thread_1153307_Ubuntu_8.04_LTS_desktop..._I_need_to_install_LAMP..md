---
title: "Ubuntu 8.04 LTS desktop... I need to install LAMP. Help!"
date: 2009-05-08
forum: Desktop Environments
---

### Post by cvl1983 on 2009-05-08
Hey, I finally figured out what was preventing my internet connection. All things connected, actually sending this from my Linux machine. The problem is, I had the commands written down to install apache, mysql, php5, etc, for a full fledged web server. I am trying to get ftp access and setup my databases by today's end.

Well, the commands are not working, and I get this prompt: 

administrator@server1:~$ sudo apt-get install lamp-server
sudo: unable to resolve host server1
[sudo] password for administrator: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package lamp-server
administrator@server1:~$ sudo apt-get install apache2
sudo: unable to resolve host server1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package apache2
administrator@server1:~$ 

Can someone maybe guide me in the right direction?

---

### Post by kanikilu on 2009-05-08
It looks like you have two problems.

The first is how you are trying to install the LAMP stack. The easiest method is:
```
sudo tasksel install lamp-server
```

Secondly, it looks like you changed your hostname and broke sudo. Check out this thread to fix it:

[http://ubuntuforums.org/showthread.php?t=1040358](http://ubuntuforums.org/showthread.php?t=1040358)

Note, obviously you'll need to fix sudo before you can install anything...

---

