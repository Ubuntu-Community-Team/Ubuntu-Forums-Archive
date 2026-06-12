---
title: "problem wireless network"
date: 2005-12-28
forum: General Help
---

### Post by dallahbillz on 2005-12-28
I'm tring to configure my wireless network card on Ubuntu 5.10, My ap is configure with wpa-psk encryption, and hidden ssid. I have downloaded wpa_supplicant and configure it properly, well I think so. When I excute wpa_supplicant through the command line with -dd argurment for debuggin. I get it scanning for ap, it founds 2 results, mine hidden ap and another one. I get ssid missmatch and it cannot associate it self with ap. My ssid name in my wpa_supplicant.conf file is LutchyNetwork. I can't showing my results of my scan because i'm on my fedora box, which almost uses the same configuration and works perfectly...

I guess because of the ssid mismatch is because of my hidden ssid. I can't find out what driver my ubuntu is using, My wireless card uses anthreos chipset.  I think my ubuntu configure itself with madwifi but i'm not sure so I configure wpa_supplicant to use madwifi but i'm not sure if this cause of it not association with hidden ssid ap

---

### Post by dallahbillz on 2005-12-28
I got it to worked, I just added a few lines in my network block of my wpa_supplicant.conf file. 

scan_ssid=1
key_mgmt=WPA-PSK

It asscaited it self and idle....:)

---

### Post by dallahbillz on 2005-12-28
Now I get it to config upon boot up, I set enable in /etc/default/wpasupplicant.
But I don't if it started and confige....

How can i check if it loaded?..

---

