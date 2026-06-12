---
title: "failed dial-up"
date: 2005-11-21
forum: Desktop Environments
---

### Post by Rhino1 on 2005-11-21
Hello, 
I am new to Ubuntu and Linux.  I managed to install a driver for a Riptide HCf modem and actually connected to the internet, albeit at a rather slow speed (14.4kbs).  that was yesterday.  Today..nothing.  I reconfigured, retyped, rebooted..still nothing.  I did manage to get it to dial in to the server, but I don't think it is logging on. No Firefox. no Evolution.  When I try to edit the config file in ppp, it shows a missing password.  Would that be normal?  Any help would be appreciated.  Writing this in XP, dual booting to Ubuntu.  Thanks in advance.

---

### Post by migueljacq on 2005-11-21
the password isn't shown in pppconfig, so that may be normal. Is it possible that it's a DNS issue?

---

### Post by az on 2005-11-22
[QUOTE=Rhino1]Hello, 
I am new to Ubuntu and Linux.  I managed to install a driver for a Riptide HCf modem and actually connected to the internet, albeit at a rather slow speed (14.4kbs).  that was yesterday.  Today..nothing.  I reconfigured, retyped, rebooted..still nothing.  I did manage to get it to dial in to the server, but I don't think it is logging on. No Firefox. no Evolution.  When I try to edit the config file in ppp, it shows a missing password.  Would that be normal?  Any help would be appreciated.  Writing this in XP, dual booting to Ubuntu.  Thanks in advance.[/QUOTE]
linuxant's drivers are proprietary.  You really need to ask them on their mailing list.  It sounds like they do not play well with udev.  That means that the driver needs to create an entry for the device everytime you boot, but it is not doing that.

---

### Post by michael_salcher on 2005-11-22
i had a HCF modem and could never get it to work properly, so i just bought an external modem on ebay that connects to the serial port. it was only $10. you might save a lot of time doing that

---

