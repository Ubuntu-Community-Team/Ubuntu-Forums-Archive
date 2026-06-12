---
title: "Problem w/ wireless in FC6"
date: 2006-11-11
forum: Fedora/RedHat and derivatives
---

### Post by drifterx on 2006-11-11
I recently got FC6, and I can't seem to get the wireless connection. I'm pretty sure it detects my device, but I don't understand whats happening, says when I attempt to activate eth1 (wireless connection), says "ipw2100 device eth1 does not seem to be present, delaying intialization." Just in case it matters, I'm using a Sony VAIO, number PCG-Z1VAP.

---

### Post by coffeecat on 2006-11-11
You need to download the ipw2100 firmware and copy it to /lib/firmware (if I remember correctly) and then select network-manager under System > Preferences > Startup Services (or whatever it's called). The ipw2100 firmware is not included in FC6 because it's proprietary and Fedora has a stricter policy about non-free software than Ubuntu. But everything else you need, including network manager and network manager gnome, comes with the default install - unlike Ubuntu.

With my ipw2200-containing laptop I had to download and install the firmware for FC6. On the other hand Ubuntu Edgy came with the firmware but I had to download network-manager. :? You takes your pick.... :)

Anyway, have a look around on [FedoraForum]("http://fedoraforum.org/forum/"). There have been several threads about getting the various Intel wireless chipsets working there.

---

