---
title: "Logging On"
date: 2005-12-30
forum: Desktop Environments
---

### Post by jlemon on 2005-12-30
I'm very new with Linux and wanted to try it out. I loaded Ubuntu 5.10 and everything has went well. I rebooted and I get a username and password screen which goes fine, then I get this. joe@ubuntu:~$     I have no clue what to do. Everything I type in says invalid password or something to that effect. I thought I might have missed something during the install so I reinstalled but get the exact same thing. Can someone help before I crawl back to XP?

---

### Post by zoiks on 2005-12-30
So you get a text-only screen with a command prompt?  (No graphics, right?)  Normally you should get a graphical screen.  Check for errors in the logs using

less /var/log/Xorg.0.log

or 

less /var/log/syslog

or 

dmesg

---

### Post by jlemon on 2005-12-31
It starts with a graphical screen, then switches to a text screen. At the top it says booting Ubuntu kernal 2.6.12-9-386. I tried less /var/log/Xorg.0.log and less /var/log/syslog and it said it wasn't a valid command line. dmesg came up with Eth0: no IPv6 router present. It then goes back to joe@ubuntu:~$

---

### Post by jlemon on 2005-12-31
I found some information and I tried some things. If I put startx as the command this comes up
fatal server error no screens found
Please consult the xorg foundation support at http:/wiki.x.org for help
XIO : fatal IO error 104
(connection reset by peers) on x server ":0.0" after 0 requests (o known processed) with 0events remaining
If I type in GDM I get
only root wants to run GDM
If I type in dpkg-reconfigure xserver-xorg I get
/usr/sbin/dpkg-reconfigure must be run as root

---

### Post by zoiks on 2005-12-31
"If I type in dpkg-reconfigure xserver-xorg I get
/usr/sbin/dpkg-reconfigure must be run as root"

Good.  Try running it as 

```
sudo dpkg-reconfigure xserver-xorg
```

sudo allows you to run stuff as root.  (Enter your user password at the prompt.)

---

