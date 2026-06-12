---
title: "Network Manager"
date: 2007-03-14
forum: Desktop Environments
---

### Post by sparty2809 on 2007-03-14
I got my laptop to work with wireless using Network-manager.  However, Network-manager doesn't pick up my wired connection.  Any ideas how I can get it to?

---

### Post by moffa on 2007-03-14
I believe it has to do with your settings in /etc/network/interfaces

Try removing the auto eth0 (or whatever card it is) line.  I know network-manager did not mess around with pre-configured cards, so maybe that is why it wont let you change the settings.

---

### Post by sparty2809 on 2007-03-15
Ok, that worked, but now how can I set the IP Address?

---

