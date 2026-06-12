---
title: "Not able to open second Gnome Session"
date: 2008-01-13
forum: Desktop Environments
---

### Post by ac7ss on 2008-01-13
After recent updates I am now unable to start second X sessions. The primary session runs fine on VT7, but any attempts to start a second user session fails with the message "unable to start GDM". This has only happened in the last couple of days. Rebooting gives no help. I am also not able to access the "Logout" menu from either the tooltray or the menu.
Nothing unusual in /var/log or on stderr.
I am running GDM.
The only error messages that I can find are> 
Jan 14 10:10:26 athena gdm[5841]: WARNING: gdm_cleanup_children: child 8359 crashed of signal 12 
Jan 14 10:10:26 athena gdm[5841]: WARNING: gdm_cleanup_children: Slave crashed, killing its children 

in both the /var/log/syslog and /var/log/daemon.log

---

