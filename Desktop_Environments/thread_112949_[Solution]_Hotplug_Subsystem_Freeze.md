---
title: "[Solution] Hotplug Subsystem Freeze"
date: 2006-01-05
forum: Desktop Environments
---

### Post by tneto on 2006-01-05
Hi

This is a poor solution but it works for me, and now i have my comp. working fine...:)

in the shell (i boot my pc whith a live cd after install kubuntu) type:

sudo rm /mnt/hdxx/etc/rcS.d/S40hotplug

hdxx is the partition where you have the ubuntu instaled

Doing this the hotplug serviçe don´t start and the pc boots normaly.

---

