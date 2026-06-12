---
title: "Gutsy Internet connection"
date: 2007-12-15
forum: Dell  Ubuntu Support
---

### Post by metallicatony on 2007-12-15
Hi All,
   Im a debian user for the past 4 years until last year.. I got Dell Vostro 1400 laptop just 2 days back..  I wanted to have only Ubuntu in my laptop after removing all the crap installed in my new laptop..
  Installation went fine.. Everything is fine - resolution, nvidia, sound, mouse pad.. everything..

  The only problem which im facing is with connecting to internet.. I have only wired connection and IP is assigned thru DHCP from my modem.. It works nicely in Windows..

  But in gutsy gibbon, when i set my eth1 (wired network card) as dhcp and restart the network service.. it tries to get an IP but finally fails saying that "NO DHCPOFFERS received".. So, im not able to connect to internet..

 Between, I want to tell you all that the card is detected properly using tg3 driver (lsmod) and lspci tells that its a Broadcom corporation Netlink BCM5906M Ethernet PCI express card.. I checked whether my network cable has been plugged properly countless times.. also i restarted my modem.. then after all the link was up, i tried restarting my network service.. then also.. its the same.. its not able to get an IP automatically and assign it to my wired network card.. 

Any thoughts on this? It looks something silly.. But it really frustrates me when internet connection doesnt work in my laptop which i bought with high hopes that i would have only ubuntu installed in it..

---

### Post by simon_is_learning on 2007-12-15
What does it say when you do ifconfig?

Maybe your wired networkcard is on eth0, mine is...

---

