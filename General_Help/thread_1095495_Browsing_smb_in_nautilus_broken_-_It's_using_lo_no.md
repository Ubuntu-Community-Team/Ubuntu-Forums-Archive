---
title: "Browsing smb:/// in nautilus broken - It's using lo not eth0"
date: 2009-03-13
forum: General Help
---

### Post by garyvdm on 2009-03-13
Hi 

Browsing to smb:/// in nautilus is broken for me. It use to work, but now it dose not. I don't know what I changed to break it.

Using wireshark - I discovered that nautilus is doing the name queries on the lo device, and not the eth0 device. 

How do I fix this?

Gary

---

### Post by garyvdm on 2009-03-13
Ah - it's working now. I had been playing with lots of .cnfg files before I posted. After I posted here, I rebooted - and it was working. Must have been a change I made that needed a reboot to take affect. I suspect that it was interfaces = eth0 in smb.cnfg

Gary

---

