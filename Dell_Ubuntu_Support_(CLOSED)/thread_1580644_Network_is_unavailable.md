---
title: "Network is unavailable"
date: 2010-09-23
forum: Dell Ubuntu Support (CLOSED)
---

### Post by epodietz on 2010-09-23
Yesterday I installed Xubuntu 10.04 on a Dell Optiplex GX520 (1 gig ram).  It booted and ran successfully. I was able to login and access the internet via Firefox. Later that evening I rebooted the machine and found surprisingly that the network was no longer available. Firefox was working offline and could not be coaxed to work online. I tried several reboots with the same result. 

Then I booted XP on the same machine and the network worked fine. NIC was assigned 191.168.1.2 and I was able to ping it from other machines. When I rebooted Ubuntu I received the same error message as before and was not able to ping that IP (makes sense).

Any ideas on how I can resolve this? I am a Ubuntu newbie so I am not familiar with the various utilities. Last time on a ...x machine was 20+ yrs ago.

Thx,

Eric

---

### Post by mikewhatever on 2010-09-24
I don't understand the problem. If the network was connected and working, but Firefox was in off-line mode, uncheck the File->WorkOffline box in Firefox. If the network wasn't connected, then Firefox had no way of going online and you'll need to troubleshoot the network, and not Firefox.

---

### Post by epodietz on 2010-09-24
Sorry I wasn't clear. When firefox said it was working offline I unchecked "Work Offline" and tried again - same result. Problem is not FireFox. So I booted XP to see if the same network hardware would work there,  under XP, and it worked fine. Rebooted ubuntu and network was still not working. Note that when I first installed xubuntu, the network (& Firefox) DID work.  So something got set or deleted or modified and I don't know how to find it and fix it.

---

### Post by mikewhatever on 2010-09-24
Can you provide some info about the networking hardware. If possible, post the outputs of the following from Xubuntu:
```
ifconfig
lshw -C network
```

---

