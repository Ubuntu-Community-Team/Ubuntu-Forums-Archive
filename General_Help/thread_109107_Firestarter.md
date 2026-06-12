---
title: "Firestarter"
date: 2005-12-27
forum: General Help
---

### Post by babwe on 2005-12-27
Im getting this error when I try to Install Firestarter...... using $sudo apt-get install firestarter................
Preconfiguring packages ...
Selecting previously deselected package firestarter.
(Reading database ... 70753 files and directories currently installed.)
Unpacking firestarter (from .../firestarter_1.0.3-1.1ubuntu1_i386.deb) ...
Setting up firestarter (1.0.3-1.1ubuntu1) ...
Starting the Firestarter firewall: failed.
invoke-rc.d: initscript firestarter, action "start" failed.
what am I doing wrong pls assist
when I try to run It after from Application/Systems Tools/Firestarter
I get this error ............
A proper configuration for Firestarter was not found. If you are running Firestarter from the directory you built it in, run 'make install-data-local' to install a configuration, or simply 'make install' to install the whole program.

Firestarter will now close.
Note I did a clean Ubuntu Install Tday
Could someone pls hlp me with these errors
Regards a New Friend In Linux

---

### Post by John.Michael.Kane on 2005-12-27
Have you tried to installing with synaptic?

---

### Post by babwe on 2005-12-27
:( Ive tried that get the same :confused:
I made a complete removal now getting somewhere.......getting this error
**Failed to start the firewall**
The device sit0 is not ready
Please check your network device settings and make shure your Internet connection is active
Its running like this
**Network**
device     type     received  sent  activity
eth0        Local          **Not activ**
eth1     Internet         **ACTIV**
Sit0      IPv6 Tunnel    **Not activ**
well Im not to shure what this device types means
Regards

---

### Post by anil_robo on 2005-12-27
Firestarter will choose one of those devices to act upon (eth0, eth1 or Sit0). IN your case, only eth1 is active, which is your wireless connection in most likelihood.

First, check if you can run firestarter manually.
1. Open a terminal (after installing firestarter) and type the following:```
gksudo firestarter
```
2. Enter your password, and press OK
3. Firestarter should open.
4. Click the preferences button, and then select your network card as eth1 (click this thumbnail to enlarge): [ATTACH]4866[/ATTACH]

Let me know if this worked for you.

---

### Post by babwe on 2005-12-28
Well at 3 this morning I got My Firestarter working :p 
**This Was The Way I Did It**
First I Deleted It Complete..
Then I ReInstalled
Went To System/Admin/Networking
Entered Password 
In Network Settings I have 3 Connections
2 Ethernet connections and 1 Modem Connection
Both Ethernet Connections Where Active (1 is on BuildIn on Motherboard (eth0) and Other  (eth1) stickon card)
I disabled (eth0) and the Modem connection)
Then I went to properties in (eth1) and set config to DHCP
and the wonder happened :KS  when I started Firestarter IT became activ:razz: 
ani_robo u where on the right track:) 
anyway conclusion Firestarter got confused by **MY**
settings on my PC
**Dont Worry**:( **Be Happy**:p 
**Stay Safe**

---

