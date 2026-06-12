---
title: "madwifi-ng: Unknown symbol in module"
date: 2006-01-17
forum: General Help
---

### Post by klepto on 2006-01-17
I've installed madwifi-ng and wpa_supplication and both are working fine..
UNTIL I reboot and I get this:

WARNING: Error inserting ath_rate_sample (/lib/modules/2.6.12-9-386/net/ath_rate_sample.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting ath_pci (/lib/modules/2.6.12-9-386/net/ath_pci.ko): Unknown symbol in module, or unknown parameter (see dmesg)

so I make install again at /usr/src/madwifi-ng and it removes the old modules
and i modprobe ath_pci and everything is good again.. UNTIL I reboot..

I put a ath_pci in /etc/modules so it will autoload on boot.

I know there's a simple issue here that I am missing.. maybe you can shed some light on it.

---

### Post by klepto on 2006-01-17
I should be writing HOWTO's because I seem to have alot of problems and yet somehow I stumble around in the dark and figure things out. My problem is that 
the modules needed to be moved to the kernel/net.

I will write the definitive guide to madwifi-ng after I get kismet working right.
This community is excellent, no matter what problem I have it has always
been solved. I swear if you don't use it you lose it. I'ts been years since I ran
slackware and I've become a m$ lackey.. for shame.

I swear I may have to remove my ntfs partition for more ext2 space :KS

---

