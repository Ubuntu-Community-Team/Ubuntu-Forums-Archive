---
title: "Use internet through virtualbox?"
date: 2009-06-27
forum: Desktop Environments
---

### Post by Handork on 2009-06-27
I have PPPoE internet, and I don't know how to enable it on my virtual host, because I have a few auto scripts which I've programmed to run for XP and I need internet for them to work, I'd appreciate it someone could help -thanks.

---

### Post by Defrector on 2009-06-28
My knowledge is limited but here is a best-effort...

VirtualBox creates a virtual NAT inside of the real machine which uses the real network connection. 

If I understand correctly, your scripts are running in the real machine.

Based on this:
*The scripts would have to get your real OS's PPoE connection going.
*set up networking config for the real OS, if necessary. 
*and then run VirtualBox, and VirtualBox will make your virtual machine see it as if a standard ethernet/LAN connection.

EDIT:
If your scripts are running in the virtual XP system, it may work if you had them ssh into your real machine, do the calls to make the PPoE connection, and then go from there.

---

