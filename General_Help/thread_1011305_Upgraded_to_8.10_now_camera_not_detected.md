---
title: "Upgraded to 8.10 now camera not detected?"
date: 2008-12-14
forum: General Help
---

### Post by Dunover on 2008-12-14
I have a Canon Power shot A510 that worked perfectly previously, I upgraded to the 8:10 now no camera, nothing... nothing to import in F-spot.. 

I ran the following lsusb

Bus 002 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 002 Device 002: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 07b2:5100 Motorola BCS, Inc. SurfBoard SB5100 Cable Modem
Bus 001 Device 004: ID 03f0:7e04 Hewlett-Packard Deskjet F4100 Printer series
Bus 001 Device 003: ID 04b3:310c IBM Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Is there anything I can do to gain access to my camera now?  Or do I have to use windoz

Thanks!
Cori

---

### Post by RomanIvanov on 2008-12-14
I had the same problem, now I use "f-spot" application. It works perfectly.

```
sudo apt-get install f-spot
```

---

### Post by Dunover on 2008-12-15
Thanks...but if you read my message it notes that I was using F-spot and am still using it with no results?

corisa

---

### Post by Izek on 2008-12-15
Does your camera have the ability to change itself into a drive instead of a camera? If so, try that, you may not be able to use F-Spot though if you do.

---

