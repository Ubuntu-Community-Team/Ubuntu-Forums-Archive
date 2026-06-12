---
title: "Wireless not working Dell Inspiron 14R N4010 / Ubuntu 11.10"
date: 2011-10-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ramkumarh on 2011-10-27
The "Additional Drivers" utility shows "Broadcom STA wireless driver".. but clicking on "Activate" fails with the following message "Sorry, installation of this driver failed. Please have a look at the log file for details: /var/log/jockey.log "

/var/log/jockey.log had this:
```
2011-10-27 01:26:05,018 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2011-10-27 01:26:05,531 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2011-10-27 01:26:05,634 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2011-10-27 01:26:06,014 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
2011-10-27 01:26:06,119 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: enabled, b43legacy: enabled
```

From "sudo lshw -C network"
BCM4313 802.11b/g/n Wireless LAN Controller

---

