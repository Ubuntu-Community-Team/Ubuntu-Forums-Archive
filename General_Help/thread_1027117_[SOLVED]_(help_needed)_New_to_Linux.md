---
title: "[SOLVED] (help needed) New to Linux"
date: 2008-12-31
forum: General Help
---

### Post by shearer_007 on 2008-12-31
Hi there. I just converted to Linux after using windows for more than a decade.

I understand there is a begineer's sub forum, but i cant seem to spot any threads there, thus im posting my question here.

1. Is there a need to install firewall and AVG for Linux? (I wanted to install zonealarm and AVG before i turn my modem on, and was too late to realise that .exe cannot be run here)

2. I cant seem to d/l wine 1.0.1 properly. Keep on getting an error msg.

---

### Post by eBoxNet on 2008-12-31
No theres not real need to install an antivirus on your ubuntu based machine...now about firewall ubuntu already have a buylt in firewall but it hasn't got any guy by default (IPTABLES),if you need an easy 2 manage firewall you can use : firestarter its not the most powerfull thing in the world but it will do the job

to install use : ```
sudo apt-get install firestarter
``` on a terminal window.
when install is done go : System -> Administration -> Firestarter

---

### Post by mikewhatever on 2008-12-31
Hi and welcome,

Here is a good read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812).

In short, none of that security software you fortify Windows with is needed.

---

### Post by shearer_007 on 2008-12-31
cool. this is amazing news for ex-window users :P

---

### Post by eBoxNet on 2008-12-31
pls mark as SOLVED
( only if we answered your questions of course )

---

### Post by shearer_007 on 2008-12-31
thanks dudes

---

### Post by 2hot6ft2 on 2008-12-31
> **shearer_007 said:**
> Hi there. I just converted to Linux after using windows for more than a decade.

I understand there is a begineer's sub forum, but i cant seem to spot any threads there, thus im posting my question here.

1. Is there a need to install firewall and AVG for Linux? (I wanted to install zonealarm and AVG before i turn my modem on, and was too late to realise that .exe cannot be run here)

2. I cant seem to d/l wine 1.0.1 properly. Keep on getting an error msg.

Ubuntu comes with Firestarter (firewall) it's in
System>Administration>Firestarter
it's a simple setup

Ubuntu comes with clamav (anti-virus) if you want a gui (graphical user interface) for it go here
Applications>Accessories>Terminal
and put this in
```
sudo apt-get install clamtk
```
hit Enter, then type in your password (it wont be displayed) and hit Enter
The it will be in
Applications>System Tools>Virus Scanner

New to Linux?
Here are some helpful things to bookmark for future reference.

Linux is Not Windows
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)

Linux alternatives to windows apps
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linux.org/apps/](http://www.linux.org/apps/)
[http://www.gimpshop.com/](http://www.gimpshop.com/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)

Everyone asks coming from windows
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

Customizing and apps
[http://ubuntuforums.org/showthread.php?t=856190](http://ubuntuforums.org/showthread.php?t=856190)
[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)

Learning Linux
[http://ubuntuforums.org/showthread.php?t=790485](http://ubuntuforums.org/showthread.php?t=790485)
[http://ubuntuguide.org/wiki/Ubuntu:Intrepid](http://ubuntuguide.org/wiki/Ubuntu:Intrepid)
[http://ubuntuforums.org/showthread.php?t=655207](http://ubuntuforums.org/showthread.php?t=655207)

Troubleshooting, multimedia and misc help
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)
[http://ubuntuforums.org/showthread.php?t=885437](http://ubuntuforums.org/showthread.php?t=885437)
[http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html](http://tazbuntu.blogspot.com/2008/07/remove-old-kernels-in-ubuntu.html)

Welcome and enjoy

---

### Post by cariboo on 2008-12-31
Had a power outage, every one beat me to it.

Jim

---

### Post by 2hot6ft2 on 2008-12-31
> **cariboo907 said:**
> Had a power outage, every one beat me to it.

Jim
Ouch, hope nothing got messed up. You still get brownie points for effort though.:KS

---

### Post by albinootje on 2008-12-31
Anti-virus software is not needed on your Ubuntu desktop, unless you worry about your Windows friends.

As firewall I really like gufw, available in Ubuntu Intrepid Ibex / 8.10 or downloadable here :  [http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

Wine : Install from the Ubuntu repositories, from firefox :  apt://wine

---

