---
title: "WiFi connection dropping out on Latitude D630 running 10.10"
date: 2010-11-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aydee on 2010-11-15
Hi, 
I am running a dell Latitude D630 with 10.10 and my WiFi connection keeps dropping out. It connects and works for 2 mins then over a 5 min period completely stops working! This is REALLY annoying!
Please Help!
Aydee

---

### Post by s3MA00RRNY on 2010-11-15
What wifi card are you using?

Run lspci in a terminal and post the results.

---

### Post by aydee on 2010-11-15
online it says bcm4328/bcm42055000
I can run the command if needed this was just faster as I have no internet in ubuntu and it takes forever to reboot windows

---

### Post by s3MA00RRNY on 2010-11-15
Go to System > Administration > Hardware Drivers (or something like that. It'll have a picture of a computer chip as the icon.) Enable the STA driver. This should help a lot.

---

### Post by aydee on 2010-11-16
> **pcdude2143 said:**
> Go to System > Administration > Hardware Drivers (or something like that. It'll have a picture of a computer chip as the icon.) Enable the STA driver. This should help a lot.
That is what I did. Prior to that I have no WiFi at all(ubuntu doesn't reconise card without that)

---

### Post by aydee on 2010-11-24
All right I Did nothing and it now works... Do I mark the thread as solved or what???

---

### Post by 14U2NV on 2011-01-11
I am current having a problem very similar.  I am running Ubuntu 10.10 on a D630, and when attempting to connect to my wireless network it will ask for the WEP.  I enter it (yes I know it is correct) and it attempts to get on.  About 30-60 seconds later, it stops and asks for the WEP again.  I am currently using the B43 wireless driver, however using the alternate driver (STA) makes my wireless card not even pick up my wireless signal at all.

---

### Post by 14U2NV on 2011-01-11
Disregard this posting, I don't have the same problem after all, plus wrong type of wireless card.

---

