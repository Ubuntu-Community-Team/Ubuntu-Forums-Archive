---
title: "Not a very Friendly Barry"
date: 2009-04-03
forum: General Help
---

### Post by version7x on 2009-04-03
First of all, thanks for any help!

I've recently attempted to install Barry for my blackberry cellphone.

I first installed the prereq's:

```
mylap$ sudo apt-get install pkg-config libusb-dev libssl-dev libboost-serialization-dev libtar-dev libgtkmm-2.4-dev libglibmm-2.4-dev libglademm-2.4-dev zlib1g-dev
```

And then installed the available packages:
```
mylap$ dpkg --get-selections |egrep 'sync|barry'
barry-util					install
barrybackup-gui					install
libbarry-dev					install
libbarry0					install
libopensync-plugin-barry			install
libopensync0					install
libpisync1					install
multisync-tools					install
opensyncutils					install

```

And I can see the blackberry on the system:
```
mylap$ lsusb
**Bus 008 Device 005: ID 0fca:8001 Research In Motion, Ltd. **
Bus 008 Device 004: ID 0781:5406 SanDisk Corp. Cruzer Micro 1/4GB Flash Drive
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 017: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 004 Device 016: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 004 Device 015: ID 413c:2513 Dell Computer Corp. 
Bus 004 Device 014: ID 413c:2513 Dell Computer Corp. 
Bus 004 Device 004: ID 0c45:63f8 Microdia 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 007: ID 0a5c:5802 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 012: ID 413c:8156 Dell Computer Corp. 
Bus 001 Device 005: ID 413c:8158 Dell Computer Corp. 
Bus 001 Device 004: ID 413c:8157 Dell Computer Corp. 
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. 
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

But when I attempt to run barrybackup - It throws up the following message:
```
No BlackBerry devices found.
```

I would love to be able to sync with Evolution and also be able to mount the microsd card to add music, etc.

Am I missing something obvious?  It seems there are a lot of people who get this to work right off the bat with little effort!

Thanks for the read!

-M

---

