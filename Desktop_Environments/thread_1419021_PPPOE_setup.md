---
title: "PPPOE setup"
date: 2010-03-01
forum: Desktop Environments
---

### Post by bugsvoid on 2010-03-01
Hi all,

I have installed Kubuntu on my machine. I need to know a KDE GUI tool to connect to internet using PPPOE DSL connection.

Currently, I have used pppoeconf to setup the connection parameters and start the service at startup. Whenever I need to connect/disconnect, I user pon/poff commands.

I tried using the KNetworkManager and added a DSL connection to it (without providing the password). However there no 'Connect' button available here.

Pls help me out.

---

### Post by fazillatheef on 2010-04-12
it will never work ... you will have to use the pppoeconf tool... i think thats why its still included in the distribution...

only if canonical(ubuntu) would make the network configuration easy and bug free... instead of making stupid themes...

another one is bluetooth tethering and network sharing.. thats another BS in ubuntu... thats why ubuntu linux will never beat windows or macos

pppoe connection through ethernet is widely used... they have very small quality check for their product.. and thats why redhat linux rules ...

---

### Post by dineshs on 2010-04-12
Try to install gpppon,
[http://newyork.ubuntuforums.org/showthread.php?t=381610](http://newyork.ubuntuforums.org/showthread.php?t=381610)

---

### Post by halj32 on 2010-04-12
> **fazillatheef said:**
> it will never work ... you will have to use the pppoeconf tool... i think thats why its still included in the distribution...

only if canonical(ubuntu) would make the network configuration easy and bug free... instead of making stupid themes...

another one is bluetooth tethering and network sharing.. thats another BS in ubuntu... thats why ubuntu linux will never beat windows or macos

pppoe connection through ethernet is widely used... they have very small quality check for their product.. and thats why redhat linux rules ...

I use the network manager
I use 3G (3connect)
use
number *99#
no name
no passwrd
APN 3internet
you can also have it auto connect or manual
other networks use different settings I only know 3G & 02

---

