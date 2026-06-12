---
title: "Dell 2405FPW Card Reader"
date: 2012-05-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by frogotronic on 2012-05-03
Hello,

  I have a 24 inch Dell 2405FPW monitor (1920x1200) and it has both USB ports and a card reader.  The output of the lsusb is below:

```
$ lsusb
Bus 007 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 413c:2005 Dell Computer Corp. RT7D50 Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0424:223a Standard Microsystems Corp. 8-in-1 Card Reader
Bus 001 Device 004: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 002: ID 0424:2502 Standard Microsystems Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

So I know the machine is seeing it, but it does not recognise any cards when inserted.  The USB works (checked via a USB drive).

Any suggestions for a driver, or a module, or a package?

Thanks,
CH

---

