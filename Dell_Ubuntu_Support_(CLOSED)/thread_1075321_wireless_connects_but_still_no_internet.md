---
title: "wireless connects but still no internet"
date: 2009-02-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Sketches on 2009-02-20
i'm kinda a newbie so no overboard comments please.

i tried the live version of Ubuntu, mint, fedora, mandriva one, etc. all have the same wireless issue. i don't have a wired connection so please keep that in mind.

i'm using a dell studio 1537 with the 
intel WIFI link 5100 (802.11 a/b/g/n 1x2 1/2 minicard)

the mandriva one live said it recognises a Broadcom Corporation 
Netlink BCM5784M Gigabit Ethernet PCle that it says won't connect 

in all distros the wireless card recognises signal and networks and it connects and says it is connected. however all the browsers get locked in an infinite cycle of loading nothing with no error message the same with package downloads. only in mandriva did an error message appear.


thanks!!!

---

### Post by knight187 on 2009-02-20
some things to check....

PSK. check that your WPA-PSK passphrase is correct, if its not you will still be able to connect but unable transfer any data across the link. This only applys if your encryption is setup to use wpa or wpa2.

IP. if your config is set to get an ip automaticly, check to see if your dhcp server is leasing you an IP. use the command ifconfig to check this.


I hope this helps a little.

Cheers.

---

