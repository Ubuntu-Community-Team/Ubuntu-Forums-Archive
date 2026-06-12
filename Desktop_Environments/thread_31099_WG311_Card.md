---
title: "WG311 Card"
date: 2005-05-01
forum: Desktop Environments
---

### Post by Joe on 2005-05-01
Has anyone had success in getting a Netgear WG311 wireless pci card working with Kubuntu?  I can get the card detected using ndiswrapper and configured the card using iwconfig but I can't can't seem to get it to pick up an ip address when i run a "ifup wlan0. 

root@ubuntu:/home/joe/Desktop # ifup wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:0f:b5:47:f6:ff
Sending on   LPF/wlan0/00:0f:b5:47:f6:ff
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by brokenflea on 2005-05-01
i had the same problem before try using these commands to see if you can bring wlan0 up initially make sure you're running no encryption on the AP

```

iwconfig wlan0 mode managed
iwconfig wlan0 <your essid> 
ifup wlan0 inet dhcp

```

or the other thing you could do is go under control center in your kde menu and go under in Internet and Networking > Wireless Network and see if you can bring up the interface through the GUI. this worked for me and you give it a shot.

---

### Post by Joe on 2005-05-01
Brokenflea those are essentially the same commands that I previously tried.  I configured the card using iwconfig but when I get to ifup, it doesn't grab an ip address from my router.

---

### Post by brokenflea on 2005-05-01
from what i remember for some reason my wlan card wasn't recognizing the AP, did you try using , i see that you used ifup but without the inet dhcp or am i mistaken. if this doesn't work try going into the gui see if you can activate the interface with gui. 

ifup wlan0 inet dhcp

i remember having the same DHCP discover messages come up everytime i tried to bring up the interface.

try this link, it helped me setup my wifi:

[http://www.ubuntulinux.org/wiki/WiFiHowto](http://www.ubuntulinux.org/wiki/WiFiHowto)

---

### Post by epb613 on 2005-05-02
[http://ubuntuforums.org/showthread.php?t=5645](http://ubuntuforums.org/showthread.php?t=5645)


I attempted to use this guide to get my Linksys card working. After following it, I still had the same troubles you´re describing. But if you look farther down the post someone writes about changing your Radio-something settings to 0 (he describes this in more detail). I did this and finally after months of no wireless, it worked! So maybe try it if it applies to you.

---

### Post by Joe on 2005-05-02
I don't appear to have a RadioState line.  All I have are these:

NdisVersion|0x50001
Environment|1
BusType|5
mac_address|XX:XX:XX:XX:XX:XX
ndis_version|NETGEAR, Inc.,04/04/2004,6.0.2.23

dot11AuthenticationMode|2
dot11BasicRateMask|1
dot11DesiredBSSType|1
dot11DesiredSSID|
dot11DesiredTxRate|0
dot11NetworkType|3
dot11SupportedRateMask|8
FBLongInterval|100
FBShortInterval|2000
LnaAgcHighThresh|55
LnaAgcLowThresh|60
LnaFftBadCorrCountThresh|100
LnaRestoreTime|600
Mode4x|0
PrivacyMode|2
WiFiAdhoc|1

---

### Post by jjross on 2005-05-03
try looking at the info in the wiki on this site and look at WifiHowTo  and WifiWithSomeoneElsesRouterHowTo.
On my computer it is listed as ath0 not lan0. After you read all the info on the wiki it might start making some sense.
I had to set the essid, the channel or frequency and couple of other things I cant really explain, but study the info on the wiki and maybe it will lead you in the right direction, it worked for me and i have the same wireless card that you have.

---

