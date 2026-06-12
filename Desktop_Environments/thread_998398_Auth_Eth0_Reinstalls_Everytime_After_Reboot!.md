---
title: "Auth Eth0 Reinstalls Everytime After Reboot!"
date: 2008-11-30
forum: Desktop Environments
---

### Post by smccarthy945 on 2008-11-30
I have Auto ETH0 configured with a static IP address. Everytime I reboot my server, it installs a 2nd AUTO ETH0 and grabs a DHCP address. I have to delete the new AUTO ETH0 and then the one with the static IP works. 

Anyway to fix this?

---

### Post by uzahnd on 2008-12-15
Same problem here. I defined a second wired connection with a static IP, but networkmanager allways tries to connect to auth eth0 (without success). As described, when I delete auth eth0, it's redefined after reboot.

Unfortuantely this is on a shared computer where I finally persuaded my co-users to try Ubuntu. This network-bug doesn't invite them to keep away from WinXP...

greets u

---

### Post by smccarthy945 on 2008-12-15
This has to be a bug in the latest version. The previous version didn't do this on the same box. As soon as I reinstalled with the new version, I had this issue.

---

