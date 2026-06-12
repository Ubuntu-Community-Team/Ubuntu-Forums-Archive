---
title: "MAC Address"
date: 2005-12-31
forum: General Help
---

### Post by Jammy_Stuff on 2005-12-31
How do I find out the MAC address of a Ubuntu box with only the base system (server) installed?

---

### Post by ape on 2005-12-31
From the command prompt (or terminal), type `ifconfig -a`.  This will show all of your available network devices.  Those physical devices will have an entry for HWaddr.  This is the MAC address.

---

