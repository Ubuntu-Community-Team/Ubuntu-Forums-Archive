---
title: "Belkin F5D6020 V3 - RTL8180 wep key problem."
date: 2005-12-27
forum: General Help
---

### Post by nicors on 2005-12-27
Hello everybody
I'm setting up my new laptop, all is working fine but i'm forced to change my wifi orinoco mini-pci card to a Belkin F5D6020 V3 because my new laptop doesn't have wifi preinstall and a free mini-pci slot.
I compiled the OpenSource drivers on my laptop after re-compile my kernel and add two encription options (see help on driver's site [http://rtl8180-sa2400.sourceforge.net/](http://rtl8180-sa2400.sourceforge.net/) ).After loading modules my card was recognized, the LED turned on but i was unable to connect with my AP. I was using the network configuration tool GUI but using console commands 

ifconfig wlan0 up
ifconfig wlan0 ap off
ifconfig wlan0 key xxxxxxxxxx

the card started to work, but it seemed that was acting as AP as default. This was solved doing a "make install" of the drivers and modifiying /etc/network/interfaces. Now the driver loads on boot and ap mode is off by default. 

The main problem now is the GUI for network configuration. If I type the wep key on it and apply changes I don't have connection, but if I look on interface properties the wep key is wrong. I.E. My key is 0001101111, I Type this on the GUI and if I do a "sudo iwconfig wlan0" my key is reported as 3030-3031-3130-3131-3131-0000-00. To correct this I need to reset the key via console and restart the connection. After reset the key is reported correctly as 0001-1011-11. This happens with all the keys I tried, doens't matter if they are numeric, alphabetich or alphanumeric.

Does anybody know how solve this problem? I hope than somebody can help me and, of course, i can help anyone who needs help with this driver posting more detailed informatioon about my experiences with this drivers.
Thanks.

---

