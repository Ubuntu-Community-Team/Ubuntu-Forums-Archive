---
title: "Ubuntu can't find my Atheros Wireless LAN card anymore!!"
date: 2009-01-12
forum: General Help
---

### Post by tee4cute on 2009-01-12
First, sorry for posting in this category. I tried to post in "Networking & Wireless" category but no one replied me.

I'm using Ubuntu 8.10 and I can access internet via wireless network since I freshly upgraded ubuntu from 8.04 -> 8.10 until yesterday.

Yesterday, I found that there's built-in driver called "ath5k" and I prefered to use it instead of madwifi driver from 8.04. So, I run "make uninstall" in madwifi package folder and also "scripts/find-madwifi-modules.sh -r" to remove all of madwifi drivers from the system.

(I fixed the /etc/modprobe.d/ settings to blacklist the ath_pci/ath_hal and unblacklist ath5k instead)

"I rebooted the system and the system can't found my wireless card anymore (lshw & lspci doesn't show my wireless card)"

I tried to reinstall the madwifi and modprobe ath_pci. So, lsmod shows that madwifi driver modules was loaded. But lshw & lspci still doesn't show my wireless card.

Anyone can help me????
(My wireless card is Atheros AR5212, IBM Z61t)

Thanks.

---

