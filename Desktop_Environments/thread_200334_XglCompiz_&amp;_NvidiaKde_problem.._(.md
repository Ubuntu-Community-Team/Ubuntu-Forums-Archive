---
title: "Xgl/Compiz &amp; Nvidia/Kde problem.. :("
date: 2006-06-20
forum: Desktop Environments
---

### Post by MasterHead on 2006-06-20
hi, i`ve been reading posts and posts for several days and i think im starting to get a bit crazy..

actually i am running kubuntu Dapper 6.06 upgraded using the official sources and this ones :

# KDE 3.5.3 Kubuntu Dapper AMD64
deb [http://kubuntu.org/packages/kde-353](http://kubuntu.org/packages/kde-353) dapper main
deb-src [http://kubuntu.org/packages/kde-353](http://kubuntu.org/packages/kde-353) dapper main

# XGL / Compiz
#deb [http://raof.dyndns.org/falcon/](http://raof.dyndns.org/falcon/) dapper eyecandy flash multimedia mythtv all
deb [http://ubuntu.moshen.de/](http://ubuntu.moshen.de/) dapper eyecandy flash multimedia mythtv all

and i`ve followed this guide
[http://ubuntuforums.org/showthread.php?p=845077](http://ubuntuforums.org/showthread.php?p=845077) , theres no prob making the nvidia drivers to work with xorg and the official repository of nvidia-glx and libgl1-mesa, until this point theres no prob, but when i change the /etc/kde3/kdm/kdmrc file and put "ServerCmd=/usr/bin/Xgl :0 -fullscreen -ac -accel glxbuffer -accel xv:fbo" ( ive tried with /usr/bin/displayconfig-restore change and without change) i restart X and everythin seems to work, but when i run glxgears i recieve this message or sort of :

name of display: :0.0
X Error of failed request: BadAlloc (insufficient resources for operation)
Major opcode of failed request: 147 (GLX)
Minor opcode of failed request: 3 (X_GLXCreateContext)
Serial number of failed request: 15
Current serial number in output stream: 16

so i have no 3d in xgl so if i try to run compiz it doesnt works... ive read somewhere that BadAlloc error might be for some libraries conflic from nvidia and mesa but no idea how to repair it or even if this is the prob.. ¿?

please somebody help me im desperate and i want this working as its really nice work..

My system is :

Nvidia 6800GT - With kubuntu repository drivers( should i try nvidia? )
Amd64X2 3800+
Motherboard Asus A8N-SLI Deluxe
1024 Mb RAM

Kubuntu is a fresh install, probably i will reintall this afternoon in order to have it all new again...

thanks a lot...

---

