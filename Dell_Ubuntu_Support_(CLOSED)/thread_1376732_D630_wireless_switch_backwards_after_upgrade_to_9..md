---
title: "D630 wireless switch backwards after upgrade to 9.04"
date: 2010-01-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by adempewolff on 2010-01-09
Hello, I just barely upgraded my main partition to 9.10--I've been primarily using a second partition with a clean install since it came out because I didn't want to deal with problems upgrading during the academic semester.  The other partition appears to have developed a bad sector right over where the ext4 fs was storing it's journal (!!) so neccesity dictated I finally upgrade the main partition.

Everything appears to have gone fine except one weird problem with the wireless: NetworkManager is imagining whichever position the wireless switch is turn to upon boot as the "off" position.

So, when I boot the laptop with the switch in the "on" position, the wifi light comes on but NetworkManager says that wireless is disabled.  When I switch it to the "off" position, the wifi light goes out, but NetworkManager starts trying to connect, eventually failing.

The only way to get the wireless to work is to boot the laptop with the switch turned off and then turn the switch on.  That way NetworkManager thinks the switch is enabled when the hardware actually is turned on.


Any suggestions on how to fix/troubleshoot this?  As the hdd is still under warranty and I'm not psyched about the bad sector I might just get a new hdd and reinstall everything, but it would be nice to figure out what caused this strange error. As soon as I have access to an ethernet cable with the computer I will file a bug on launchpad against it.

---

### Post by adempewolff on 2010-01-16
Problem appears to be fixed.  I manually downloaded the network-manager and network-manager-gnome packages from the repositories.  Turned off network manager, uninstalled the packages, then reinstalled them from the packages I downloaded. Didn't even need to restart to get networking working again, but on the next restart the switch problem appears to have disapeared!

---

