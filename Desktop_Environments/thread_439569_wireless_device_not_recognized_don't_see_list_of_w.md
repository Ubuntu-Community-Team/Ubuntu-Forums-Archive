---
title: "wireless device not recognized/ don't see list of wireless names."
date: 2007-05-10
forum: Desktop Environments
---

### Post by ak_saravanan on 2007-05-10
Hi,

I am a first time linux installer.

Got a IBM T23 laptop and installed ubuntu 2.6 (released on apr 15th, 07) .

I was able to connect through ethernet.
But under network manager, i don't see any wireless services available..

when i tried check the properties for wireless device i don't see a it is lited

got 3 entries...
wired connection (wlan0), wired connection (eth0), modem connection.

i got a intersil prism 2.5 wireless card inbuilt in it.

checking on wirelss problems from this site, suggested to try ndiswrapper and so i tried install ndiswrapper utils and commons. but i couldn't find .inf, .sys files for my driver.


i also tried to comment out /etc/network/interfaces file to just have entry with lo

commenting out other entries like etho, etho1 etc... 

please help how to activate my wireless.

thanks
AK

---

### Post by ak_saravanan on 2007-05-18
I was able to fix the problem.

comment all lines except for lo in /etc/network/interfaces

add blacklist for orinoco_pci, prism2_pci to /etc/modprob.d/blacklist

put these in a startup script

ifconfig wlan1 down
iwconfig wlan1 essid MYSSID  key MYKEY
ifconfig wlan1 up
dhclient3 wlan1

---

### Post by PacerTracer on 2007-05-18
Ok I don’t want to offend any body by messaging in some one else’s forum but I am a total nube to Linux. I am an A+ & CCNA but I don’t know a darn thing about Linux. My friend got me messing around with it. I know it is asking allot but if some one would be willing to show me the rope I would really appreciate it and I would be more then willing to learn and/or teach you anything I know that you would like to learn in return.
With hopes that somebody can help me out... Thanks in advance.
Sincerly, 
Your Fellow Linux User
PacerTracer

---

### Post by elfstone214 on 2007-05-18
> **PacerTracer said:**
> Ok I don’t want to offend any body by messaging in some one else’s forum but I am a total nube to Linux. I am an A+ & CCNA but I don’t know a darn thing about Linux. My friend got me messing around with it. I know it is asking allot but if some one would be willing to show me the rope I would really appreciate it and I would be more then willing to learn and/or teach you anything I know that you would like to learn in return.
With hopes that somebody can help me out... Thanks in advance.
Sincerly, 
Your Fellow Linux User
PacerTracer

Are you referring about learning Linux in general? I have only been using Linux for about a month and feel I feel pretty confident in it now. In fact I am 100% Linux converted now and completely wiped out my Windows partition. So basically what I am saying is really give it a try, anyone can do it. You can find a lot of what you need by simply googling your problems or searching these forums.

and remember the magical command
> sudo apt-get install *programname* ;)

---

