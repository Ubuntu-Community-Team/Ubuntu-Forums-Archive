---
title: "installing windows drivers for hardware not using wine??"
date: 2009-03-18
forum: General Help
---

### Post by 8th Unknown on 2009-03-18
system  laptop amd 64  running Ubuntu 8.04 32 bit (because wireless driver is 32 bit) 

i have a midi padKontrol  i tried installing the drivers in wine but that didn't work 

because i cant run the install for the driver 

(no administrator privileges and wont run in 98/Me mode) 

ive posted on wine hq and 

it seems you canot instal drivers with wine? i think

so im wondering if their is a way to install the driver with say "ndiswrapper" 

(like i did with my wireless issues) 

or if i can run the .exe in ubuntu and install the driver that way.

---

### Post by hikaricore on 2009-03-18
You can not install drivers via WINE, even in cases where the install works it doesn't do anything.
Windows drivers can not and will never be able to be used on Linux outside of the ndiswrapper environment.

Have you searched the forums for info on setting up wireless drivers this way?  There have been tons of threads on the topic and several howtos.

---

### Post by 8th Unknown on 2009-03-18
thnx for the reply i did fix my wireless already with ndiswrapper but when i tried to do the same with a driver for my drumpad it messed up my wireless i think im going to TRY to make a dual boot visa ubuntu system now because i need REASON as well.

---

### Post by Chesamo on 2009-03-18
There isn't a way to use Windows drivers in Ubuntu. NDISwrapper only works with wireless drivers (NDIS stands for Network Driver Interface Specification, the Windows spec for networking).

Sorry.

---

### Post by theozzlives on 2009-03-18
Is this drumpad USB? If so, you can install Windows inside a [VirtualBox]("http://www.virtualbox.org/") and access your drums that way.

---

