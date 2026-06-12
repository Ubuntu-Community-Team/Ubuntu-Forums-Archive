---
title: "Karmik 64 Samba start issues"
date: 2009-11-24
forum: Desktop Environments
---

### Post by razor7 on 2009-11-24
Hello...i have installed Karmik x64 (fresh install) and installed / configured samba and winbind (because i use openDNS), everything goes OK, but after reboot, i can not see any share from ANY PC (windows/linux), so in the host machine, I ran /etc/init.d/samba restart...and it says "process id 1506 not found" (or similar), so I go to the System Monitor, in the Process Tab, i terminate the two smbd processess, and run /etc/init.d/samba start and all goes ok...even using "smbtree" command in the host machine.

How can I solve this?

Thanks a lot!

---

