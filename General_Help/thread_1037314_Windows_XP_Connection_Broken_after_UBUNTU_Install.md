---
title: "Windows XP Connection Broken after UBUNTU Install"
date: 2009-01-11
forum: General Help
---

### Post by frlando on 2009-01-11
I have a dsl connection, desktop, netgear wireless router and laptops. I installed UBUNTU on my desktop using WUBI. After install, worked under UBUNTU OS using Mozilla. After reboot, needed to work under XP OS, however I could not connect to the internet. Did everything I could think of. Finally uninstalled UBUNTU, turned off all equipment (router, modem, desktop), turned back on and was able to reconnect in XP. Would like to get UBUNTU back and work with it until comfortable then get rid of XP altogether, but can't afford to be w/o connection under XP in the interim. Can anyone tell me how I can maintain my internet connection using both UBUNTU and XP on the same computer? I looked for this answer in other forums but couldn't find anything.
Any help? THanks.
Fran

---

### Post by chex_m8 on 2009-01-11
It's going to be difficult to trooubleshoot the problem now that you've uninstalled ubuntu.
i would reinstall ubuntu so we can help.
my guess is that when you went back to xp you were not getting an ip address from your DHCP server.
you could try this in windows
ipconfig /release
ipconfig /renew

again, we cant help if there is no problem to troubleshoot

---

