---
title: "Laptop wireless problems"
date: 2006-04-28
forum: Desktop Environments
---

### Post by Paradoxx on 2006-04-28
Hi. I'm running kubuntu 6,06 drapper. 
I've got a external netcard (Ovislink Airlive WL-8000PCM). I'm using ndiswrapper to get the driver running, and the status og ndiswrapper is Driver present, Hardware present.

When useing kWiFimanager, i can se signal strength og names of nearby networks, and i think connect to them.

But i am not giving a IP and when im looking in networksettings it tells me that the card is disabeled... and i can't enabel it. 

Can anyone help ?

---

### Post by gingermark on 2006-04-28
*** Deleted due to complete and utter stupidity (and a link to **wired** network troubleshooting - sorry ***

---

### Post by ibanez88 on 2006-04-29
I'm having similar problems in with kwifimanager.  Network-manager in Gnome seems to work better (at least with my card - ipw2200).  However its just slow as heck so it may still be faster and more reliable to edit the interfaces file by hand.

In response to your question, try typing

sudo dhclient

and see if you get a lease.  This seemed to work with me using kwifi however I couldn't get it to execute this command automatically on startup.  Tried executing a script on connect... still no dice.  So I guess its back to hand-editing for me for the time being.

However you might have more luck.

---

### Post by Paradoxx on 2006-04-29
[QUOTE=ibanez88]I'm having similar problems in with kwifimanager.  Network-manager in Gnome seems to work better (at least with my card - ipw2200).  However its just slow as heck so it may still be faster and more reliable to edit the interfaces file by hand.

In response to your question, try typing

sudo dhclient

and see if you get a lease.  This seemed to work with me using kwifi however I couldn't get it to execute this command automatically on startup.  Tried executing a script on connect... still no dice.  So I guess its back to hand-editing for me for the time being.

However you might have more luck.[/QUOTE]

When runing the command i get: 

Listening on LPF/wlan0/00:4f:62:01:aa:ac
Sending on   LPF/wlan0/00:4f:62:01:aa:ac
Listening on LPF/eth0/00:c0:9f:68:d6:e1
Sending on   LPF/eth0/00:c0:9f:68:d6:e1
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
receive_packet failed on wlan0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

doesn't seem to work.... :( any others idears ?

---

