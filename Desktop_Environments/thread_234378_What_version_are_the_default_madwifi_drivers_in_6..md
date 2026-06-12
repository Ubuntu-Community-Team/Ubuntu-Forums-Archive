---
title: "What version are the default madwifi drivers in 6.06?"
date: 2006-08-11
forum: Desktop Environments
---

### Post by Cytomax on 2006-08-11
Hello all i am sorta new to linux and just finished installing 6.06 using the DVD version.  I bought a Netgear WG511T (Atheros Chipset) which works great out of the box but i want to try and fool around with aircrack-ng so i have some questions.   

**Question #1**
I read on some places that i might have to patch my drivers with madwifi drivers in order to use packet injection ([http://www.turkeyfarm.net/blog/2006/06/22/cracking-wep-with-linux-actually-works/)](http://www.turkeyfarm.net/blog/2006/06/22/cracking-wep-with-linux-actually-works/)). 

but


I also read that 
"Ubuntu ships madwifi in the restricted component, which is enabled in the default install. Madwifi chipsets should therefore ‘just work’.

In case you did a manual install, try installing linux-restricted-modules-$(uname -r) and that’s it.
6.06 Drapper Drake ¶

There appears to be a bug in the udevplug madwifi-ng scripts, which causes a large delay on startup; This will be fixed in the release soon, and there is a fix here, for now: [https://launchpad.net/distros/ubuntu/+source/udev/+bug/46048](https://launchpad.net/distros/ubuntu/+source/udev/+bug/46048) "
[http://madwifi.org/wiki/UserDocs/Distro/Ubuntu](http://madwifi.org/wiki/UserDocs/Distro/Ubuntu)

All i did to install Ubunutu was partition my drive into 2 (first partition is WinXp Pro) and used the second partition for Ubuntu.  I booted off the dvd Clicked the Install Icon answered a few questions and BAM... like magic it was done...

So do i have to patch? 

**Question #2**

Where can i locate these drivers to see what version they are?

**Question #3**

I am also confused as to what chipset i have

According to [http://madwifi.org/wiki/Compatibility#WG511T](http://madwifi.org/wiki/Compatibility#WG511T)
I have the following:
**Chipset:	AR5001 (V1&V2=5212) (V3=5213A) (b/g)**

but 

According to [http://customerproducts.atheros.com/customerproducts/](http://customerproducts.atheros.com/customerproducts/) (search for netgear)
I have the following:
Product Name - 108 Mbps Wireless PC Card - Model WG511T
Product Type - Cardbus
Technology Band - 802.11b/g
**Atheros Chipset - AR5005GS**
Advanced Features - Super G

So which chipset is it..
**Chipset:	AR5001 (V1&V2=5212) (V3=5213A) (b/g)**
or
**Atheros Chipset - AR5005GS**

Thanks in Advance
Eddie

---

### Post by Ramses de Norre on 2006-08-11
This should reveal your chipset: ```
lspci|grep -i atheros
```

I'm not sure about your other questions..

---

### Post by Cytomax on 2006-08-11
I still dont know Question #1 or Question #2

Question #3 is answered...
You are the MAN Ramses de Norre...

**Ethernet Controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)**

Thanks in Advance
Eddie

---

### Post by superm1 on 2006-08-29
I do have a AR5212 in my thinkpad.  I'm using what I believe is madwifi-old.

This is the info spit out by dmesg on startup (including versions)

```
[17179601.156000] ath_hal: module license 'Proprietary' taints kernel.
[17179601.156000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179601.764000] ath_rate_sample: 1.2
[17179601.784000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179602.096000] ath0: 11a rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179602.096000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179602.096000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179602.096000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179602.096000] ath0: mac 5.6 phy 4.1 5ghz radio 1.7 2ghz radio 2.3
[17179602.096000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17179602.096000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179602.096000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17179602.096000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17179602.096000] ath0: Use hw queue 8 for CAB traffic
[17179602.096000] ath0: Use hw queue 9 for beacons
[17179602.096000] ath0: Atheros 5212: mem=0xc0210000, irq=11
```

I'm not particulary sure how to even enable madwifi-ng.

---

