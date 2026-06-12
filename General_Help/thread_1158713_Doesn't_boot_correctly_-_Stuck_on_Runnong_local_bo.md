---
title: "Doesn't boot correctly - Stuck on Runnong local boot scripts"
date: 2009-05-13
forum: General Help
---

### Post by Curbside on 2009-05-13
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

### Post by zvacet on 2009-05-14
After message 

> *Running local boot scripts (/etc/rc.local) [ OK ]

type startx and if that doesn´t help type

```
sudo /etc/init.d/gdm start
```

---

### Post by Curbside on 2009-05-14
when i type startx i get something like..

Markers: (--) probed, (**) from config file, (==) default setting,
          (==) from command line, (!!) notice, (II) informational,
          (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/ar/log/Xorg.0.log". Time: Thu May 14 15:28:27 2009
(==) Using config file: "etc/X11/xorg.conf"
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
MTSC PAL
finished output detect: 0
finished output detect: 1
(EE) RADEON(0): No connected devices found!
finished all detect
before xf86InitialConfiguration
(EE) RADEON(0): No valid modes.
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found

waiting for X server to begin accepting connections
giving up.
xinit: Connection reset by peer (errno 104): Unable to connect to X server 
xinit: No such process (errno 3): Server error.
xauth: error in locking authority file /home/brad/.Xauthority

When i do sudo /etc/init.d/gdm start, I get:
*Starting GNOME Display Manager...[OK]

then it doesn't do anything, and just hangs there.

---

### Post by Curbside on 2009-05-14
bump

---

### Post by Curbside on 2009-05-14
bump

---

### Post by zvacet on 2009-05-15
It seams that your graphic card is not recognized.Try

```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

---

