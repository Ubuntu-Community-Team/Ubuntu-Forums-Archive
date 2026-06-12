---
title: "control center root login problem"
date: 2005-06-23
forum: Desktop Environments
---

### Post by V1xIII on 2005-06-23
pardon my linux noobness, but i was originally trying to fix my problem with web pages loading slowly by doing what was mentioned in the thread [http://ubuntuforums.org/showthread.php?t=536](http://ubuntuforums.org/showthread.php?t=536)  

I went into control center, internet&network, network settings, click on administrator mode, the run as root box pops up, i put in my password, it says loading, then takes me either back to the control center welcome page, or the internet and networking welcome page and never logs me in.  what is going wrong?

(also, i'm not sure how to get into root from the login screen, its not taking root as a username like i'm used to from my limited prior experience with mandrake)

---

### Post by Dragonfly_X on 2005-06-23
You should update to KDE 3.4.1 ! That will fix the admin mode problem.

[http://www.kubuntu.org/hoary-kde-341.php](http://www.kubuntu.org/hoary-kde-341.php)

---

### Post by IchBin on 2005-06-23
[QUOTE=Dragonfly_X]You should update to KDE 3.4.1 ! That will fix the admin mode problem.

[http://www.kubuntu.org/hoary-kde-341.php](http://www.kubuntu.org/hoary-kde-341.php)[/QUOTE]
 KDE 3.4.1 does not fix this bug. There has been quite a few posts in this forum about this. Do a search and you'll see.

---

### Post by Dragonfly_X on 2005-06-23
[QUOTE=IchBin]KDE 3.4.1 does not fix this bug. There has been quite a few posts in this forum about this. Do a search and you'll see.[/QUOTE]

Worked for me... :razz:

---

### Post by tikal26 on 2005-06-23
form a root terminal typ kontrol

---

### Post by V1xIII on 2005-06-23
well, i've searched it out on the forums, and i've attempted to allow root login from kcontrol (i know most of you say logging in as root is bad) but administrator login doesnt work for anything in control center so i cant enable root login... grrr  ](*,)

---

### Post by Pcghost on 2005-06-23
There should be no need for root login, use sudo instead. From a console type sudo kcontrol, give your password, then it should launch in Administrator mode.

---

### Post by d4n on 2005-06-23
[QUOTE=Pcghost]There should be no need for root login, use sudo instead. From a console type sudo kcontrol, give your password, then it should launch in Administrator mode.[/QUOTE]

I have the same problem and I've tried this and I just get:

> DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /root/.DCOPserver_scandium__0
and start dcopserver again.
---------------------------------

DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
WARNING: DCOP communication problem!
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
FATAL: DCOP communication problem!
kdeinit: Communication error with launcher. Exiting!
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
DCOPClient::attachInternal. Attach failed Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
ERROR: KUniqueApplication: Can't setup DCOP communication.

I'm a complete noobie so any help welcome.

---

### Post by dhanish on 2005-06-23
[QUOTE=d4n]I have the same problem and I've tried this and I just get:



I'm a complete noobie so any help welcome.[/QUOTE]
 Try using kdesu kcontrol instead of sudo.

---

### Post by dejitarob on 2005-06-23
I've never actually had to go into "Administrator Mode". I am able to change anything by just opening it up normally. Have you tried it without Admin mode? Btw, that thread is very old. Is your connection just slow loading websites? Have you tried a bandwidth test? I had a issue with my box at work and my NIC. Cisco routers apparently don't autonegiotate well with certain 3COM cards. It worked fine it windows, but when I used Ubuntu the upload was extremely slow, causing website loading times to be very long.

---

### Post by Fintan on 2005-06-24
[QUOTE=dhanish]Try using kdesu kcontrol instead of sudo.[/QUOTE]
 Had the same problem: do alt+F2 then type kdesu konqueror confirm/type your root password and access the control center from there. Somehow it does not always work with kdesu kcontrol from the terminal.

Hope that helps
Fintan

---

### Post by d4n on 2005-06-24
That worked first time, cheers.

---

