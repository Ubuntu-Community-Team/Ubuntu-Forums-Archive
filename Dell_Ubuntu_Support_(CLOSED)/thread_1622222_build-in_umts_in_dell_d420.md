---
title: "build-in umts in dell d420"
date: 2010-11-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pleasepressanykey on 2010-11-15
Hey, 

I tried to get buit-in UMTS module in a Dell Latitude D420 to work. I installed a fresh 10.10, everything worked fine... it detected the UMTS-card, and it worked. But always after a few minutes it quits working, droppeds the connection and it wont reconnect until I restarted the PC. 

Then I read somewhere that the WICD network manager in combination with the UMTSmon might work better than the built-in one. So I replaced the default network manager and installed UMTSmon. I didn't manage to to get UMTS to work in any way again after this step, although the wired network still works. It detects the network and signal strength etc but is not able to connect.

 After fixind some problems there I am stuck now. UMTSmon says 

```
Using interface ppp0
Connect: ppp0 <--> /dev/ttyUSB1
LCP: timeout sending Config-Requests
Connection terminated.
Terminating on signal 15
Modem hangup
```

The card seems to be a Novatel Expedite EU730, at least UMTSmon is saying that.

Anyone has an idea? I really don'tk now what I could do additionally. If any additional info is required I will serve it as quick as possible, I hope I didn't forget anything.

Thanks in advance!

---

