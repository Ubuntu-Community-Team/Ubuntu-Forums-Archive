---
title: "Booting Problems-Stuck on Running local boot scripts"
date: 2009-05-12
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Curbside on 2009-05-12
Hello, I'm very very new to linux but I've had Ubuntu 8.04 installed on my 2002 Dell for about half a year now and never had any problems with it, but last week when I tried to turn it on, it did not boot normally.

It went to a screen with a black background and white text and said:

*Starting acnac(h)ronistic cron anacron [ OK ]
*Startomg derred execution scheduler atd [ OK ]
*Starting periodic command scheduler crong [ OK ]
*Enabling additional executable binary formats finfmt-support [ OK ]
*Checkings battery state...
/dev/sda:
setting Advanced Power Management level to 0xfe (254)
[ OK ]
*Running local boot scripts (/etc/rc.local) [ OK ]

_

It hangs on running local boot scripts and does nothing...I've tried doing Control Alt F2 to get the tty2 and logging in, then doing startx but i comes up with a lot of failures and errors (more info on this if needed)

Some things I've randomly tried: 
booting it from a CD
Reinstalling it from a CD 
booting it in recovery mode but it just does the exact same thing
sudo dpkg-reconfigure -phigh xserver.org and it doesn't work
sudo apt-get update and it doesn't work
dhclient eth0 and it doesn't work
sudo aptitude install xubuntu-desktop and it doesn't work

If you need information on the errors when i run the command i can give you it but i didn't want to list every error incase the command wasn't related to the problem. Any help is needed and if you try to explain something for me to to, please do it step by step and with great detail.

---

### Post by Curbside on 2009-05-13
bump

---

### Post by Curbside on 2009-05-13
bump

---

### Post by Curbside on 2009-05-13
bump

---

