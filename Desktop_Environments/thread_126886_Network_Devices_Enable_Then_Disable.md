---
title: "Network Devices Enable Then Disable"
date: 2006-02-07
forum: Desktop Environments
---

### Post by anmlcrckrs on 2006-02-07
On my laptop I've got an internal wireless card and a wired port and whenever I try to enable them, they go green and say enabled for 2 seconds and then turn back to disabled.  What am I to do?

---

### Post by gonesolo on 2006-02-08
I had the same problem with my wireless card after I installed Kubuntu.

eventually I found - go to a bash prompt and configure from there. This is what I did

SUDO IWCONFIG RA0 ESSID *NETWORKNAME*

SUDO IFDOWN RA0

SUDO IFUP RA0

Once I did this my network connection worked as it was supposed to and after a reboot my settings were saved automatically so it started during boot time.

---

### Post by NeoChaosX on 2006-02-08
What he said. The KDE network tools are currently crap. You're better off using the commandline tools to configure network right now.

---

### Post by essexman on 2006-03-19
This is a bug please go to [https://launchpad.net/distros/ubuntu...onf/+bug/35129]("https://launchpad.net/distros/ubuntu/+source/knetworkconf/+bug/35129")

and add a "me too" to get developers to fix it

---

