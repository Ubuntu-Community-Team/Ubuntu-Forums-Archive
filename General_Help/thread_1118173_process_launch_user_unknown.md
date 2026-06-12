---
title: "process launch user unknown"
date: 2009-04-06
forum: General Help
---

### Post by termdex on 2009-04-06
I've setup dhcpd.conf to include the rndc.key file from bind. I've included the dhcpd user account in the bind group and the bind group has read permission on the rndc.key file.

Yet when dhcpd launches it fails to open rndc.key responding with "Permission denied." However if I change the permissions on rndc.key to 'o+r' dhcpd obtains permission.

This tells me that dhcpd is being run as some account other than root or dhcpd. I've checked the init.d script for dhcpd but I don't see where the launch account is specified. start-stop-daemon is used to launch dhcpd but its chuid switch is not used.

Any ideas?

---

