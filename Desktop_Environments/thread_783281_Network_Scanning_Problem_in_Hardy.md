---
title: "Network Scanning Problem in Hardy"
date: 2008-05-05
forum: Desktop Environments
---

### Post by fdimmling on 2008-05-05
My Epson scanner works perfectly on the local computer it is connected to. However Xsane on a remote computer does not find a scanner. Everything is setup according to the (German) Wiki article. /var/log/daemon on the host says:

fd-desktop saned[11198]: init: access granted to saned-user@192.168.0.5

saned on the host is member of the scanner group, as are the users on the client computers. The group saned has no users.

Any hints?

Friedrich:confused:

Scanning is possible if you set user and group both to root in the saned line /etc/inetd.conf - in contrast to what is written in the HowTo and what should be for security reasons.

---

### Post by guardian_de on 2008-05-24
Before Hardy access to scanners was granted by udev, giving access to the scanner group.

Since Hardy HAL and PolicyKit grant access to scanner devices for session users.

See [https://bugs.launchpad.net/ubuntu/+bug/229343](https://bugs.launchpad.net/ubuntu/+bug/229343) for a solution.

---

