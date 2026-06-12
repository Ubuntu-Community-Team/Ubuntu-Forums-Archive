---
title: "Xbox 360 Controller driver problems"
date: 2009-01-10
forum: Gaming &amp; Leisure
---

### Post by snoopy12533 on 2009-01-10
I followed the directions i found to install a driver for the xbox 360 controllers here [https://help.ubuntu.com/community/Xbox360Controller]("https://help.ubuntu.com/community/Xbox360Controller") But all i get is this in terminal when i use the make command

[email]paul@Ubuntu:~/.xpad[/email]$ make
make modules -C /usr/src/linux-headers-2.6.27-11-generic SUBDIRS=/home/paul/.xpad
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-11-generic'
scripts/Makefile.build:41: /home/paul/.xpad/Makefile: No such file or directory
make[2]: *** No rule to make target `/home/paul/.xpad/Makefile'.  Stop.
make[1]: *** [_module_/home/paul/.xpad] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-11-generic'
make: *** [all] Error 2
[email]paul@Ubuntu:~/.xpad[/email]$ 

I am a linux noob and could use some help

---

