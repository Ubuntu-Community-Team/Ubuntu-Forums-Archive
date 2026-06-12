---
title: "question about how hibernate/standby works"
date: 2009-01-06
forum: General Help
---

### Post by Kain000 on 2009-01-06
I was wondering if anyone knew exactly how hibernate and standby worked, in terms of allowing daemons to be actively listen on their ports while in standby.

The goal is to be able to have my desktop in standby to conserve power, but when a connection request comes in on the FTP port it would wake up and connect.    
Is this possible?

---

### Post by sdennie on 2009-01-07
It's possible, yes.  The functionality is called Wake On Lan.  The information in this thread might be useful: [http://ubuntuforums.org/showthread.php?t=202174](http://ubuntuforums.org/showthread.php?t=202174).

---

### Post by Kain000 on 2009-01-08
Ahh the WOL, I've messed with this before, but without luck from outside the network.   I want to be able to leave my server powered on but waiting for the signal (Magic packet) to come alive.  Wol would be just right with a timeout script to put it back to sleep, but I cant get the packet to pass threw my gateway.  

I used a program called wake on lan with linux, and works fine from inside the network, but outside the lan even when I sent the packet to a port that is fowared to the server, it wont wake up!   and I struggled with this for weeks before just giving up in frustration.   

Bottom line is I want a server to be waiting for me to access where ever I am, but without going 100% in the meantime sucking power.

any ideas about wake on lan or otherwise?

---

