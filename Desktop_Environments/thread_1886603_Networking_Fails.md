---
title: "Networking Fails"
date: 2011-11-25
forum: Desktop Environments
---

### Post by uniman on 2011-11-25
Hi Guys Here is my problem, I have a HP6000 1 of 30 running Ubuntu 11.04. Network configured during install all working no problem but this one HP looses the network. Have run lshw -C network, checked most if not all files to do with networking all appear to be the same as the HP next to it. This has happened in the past and I just rebuilt it, now I want to know why it fails.:confused:

---

### Post by Lampi on 2011-11-25
You can fix this with a better udev rule:

cat /etc/udev/rules.d/70-persistent-net.rules 
```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="*", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
```

compare this to the rule you have to understand what is happening: with the default rule each MAC address will get it's own eth device instead of eth0, mine keeps all of them at eth0

---

### Post by uniman on 2011-11-25
Looked into this but does not fix the problem

---

### Post by Lampi on 2011-11-25
how does /etc/network/interfaces look like?
what happens if you request an IP manually using dhclient eth0?

give some more input what else you tried and how your setup looks like, otherwise it's next to impossible to help.

---

### Post by uniman on 2011-11-25
I need to go and start work rebuilding some workstations in the digital forensic lab so will start this again on Monday

---

