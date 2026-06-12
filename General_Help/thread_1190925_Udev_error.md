---
title: "Udev error"
date: 2009-06-18
forum: General Help
---

### Post by potam on 2009-06-18
Hello all,

I am using Jaunty. I have an USB device, normally appear in lsusb:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 061: ID 16c0:05dc VOTI 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
I am talking about the VOTI device. Normally root is the owner of the device file, that is I want to change. I created a file under /lib/udev/rules.d called 60-programmer.rules. Content:
```

SYSFS{idVendor}=="16c0", SYSFS{idProduct}=="05dc", GROUP="users", MODE="660"

```
When I restart udev (sudo /etc/init.d/udev restart) and replug the device, Ubuntu creates the device file with the correct owner (users), but the device no longer visible in lsusb, so I can not use it. Lsusb output after adding the rules file and restarting udev:
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

What is the problem?

---

### Post by potam on 2009-06-19
Moving the file 60-programmer.rules to 40-programmer.rules solved my problem.

---

