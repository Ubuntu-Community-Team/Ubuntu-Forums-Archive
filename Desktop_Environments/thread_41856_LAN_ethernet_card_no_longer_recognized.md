---
title: "LAN ethernet card no longer recognized"
date: 2005-06-15
forum: Desktop Environments
---

### Post by stepore on 2005-06-15
sorry for the cross-post to desktop support and networking.

I've got Ubuntu Hoary on an IBM Thinkpad with a built-in network card, which was working without any problems what so ever.

here's the thing; for the last 5 months or so i've been using a Netgear wireless card exclusively. In fact, I actually upgraded from Ubuntu Warty 4.10 to Hoary 5.04 using apt-get over the wireless. after upgrading i've been happily using the wireless card. yesterday, for the first time since the upgrade, i tried to plug a network cable (from the router) to the LAN card and it no longer works. it doesn't seem to even be recognized anymore. for some reason, during the update Ubuntu switched the card designations around. eth0 was the LAN card and eth1 was the wireless. but now eth0 is the wireless. i guess because it was plugged in at the time of the upgrade.

lspci shows this:
0000:00:03.0 Ethernet controller: 3Com Corporation 3c556B CardBus [Tornado] (rev 20)

lsmod | grep 3c59x
3c59x	    37160  0

in /etc/network/interfaces i've got this:
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
name Ethernet LAN card

iface eth0 inet static
name Wireless LAN card
wireless_essid xxxxxxxxx
wireless_key xxxxxxxxxx
wireless_mode Managed
wireless_rate 54M auto
address 192.168.2.100

what's left to do to get the LAN card to be recognized? is it a hardware detection problem, caused by the upgrade, or just something i'm missing in a configuration file? the wireless works fine, as eth0. i've tried swapping the cards around (wireless as eth1 and LAN card as eth0) but it didn't work. 

ubuntu's network-admin tool only shows the wireless card and the built-in modem. there's no 'add device' option to the gui tool.

tips on what i can do to get the LAN card to work?

---

