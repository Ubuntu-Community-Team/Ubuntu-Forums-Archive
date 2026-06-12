---
title: "Time-admin crashes"
date: 2005-12-20
forum: General Help
---

### Post by lisigef on 2005-12-20
Each time I right-click on the clock on my panel and select Adjust Date & Time, the window loads but there is nothing in it and it freezes. I have to force-quit. I tried rebooting several times, same thing. This is a fresh install of Breezy Badger.

Thanks

-Lisi

---

### Post by BathroomNinja on 2005-12-20
I'm willing to bet that it's somehow trying to connect to the internet and update it's time.  Noticing your problem with connecting to the internet, I bet since your not connecting, it's not seeing the time server and it's locking up the computer.  Have you tried this AFTER you have connected to the internet, or are you doing it BEFORE you get on?


EDIT.  I need to remember what I read.

---

### Post by lisigef on 2005-12-20
Definitely after - connecting to the Internet is pretty much the first thing I do :)

---

### Post by Kamakzie on 2006-02-16
Mine is crashing too.  I am running a dapper install.  I get this when I run through terminal..

 sudo time-admin

** (time-admin:18881): WARNING **: Could not open */usr/share/zoneinfo/zone.tab*

** ERROR **: Unable to load system timezone database.
aborting...

Any ideas?

---

### Post by joe_gosse on 2006-02-20
I am also getting the same problem. 

> ** (time-admin:19802): WARNING **: Could not open */usr/share/zoneinfo/zone.tab*

---

### Post by davebgimp on 2008-03-10
I had the same problem. I thought it might be my firewall (firestarter manages it). I temporarily disabled it and it immediately worked. Try opening NTP (port 123) and see if that works out.

---

