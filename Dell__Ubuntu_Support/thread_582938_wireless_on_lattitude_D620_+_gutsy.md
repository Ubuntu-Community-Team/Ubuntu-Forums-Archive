---
title: "wireless on lattitude D620 + gutsy"
date: 2007-10-20
forum: Dell  Ubuntu Support
---

### Post by cytg on 2007-10-20
Installed fine
under the network icon i have a menu option called wireless connection, but i cannot select it.
under system->network wireless is also configured and set to "roaming" ..

my "problem" .. does not connect to my open unencrypted home wifi .. also i cannot find a tool that displays networks within range etc.
(i'll try to connect to "other wireless networks" and enter the correct name, yet it still doesnt work).

plz ?
:)

---

### Post by arash.oio on 2007-10-20
check this:
[http://ubuntuforums.org/showthread.php?t=257684](http://ubuntuforums.org/showthread.php?t=257684)
maybe it is useful

---

### Post by cytg on 2007-10-20
thanks i did that for 7.04, however stuff is recgonized out of the box here, so i figured it was good (plus a feature of 7.10 was supposedly better broadcom support).

So im seeing the network interface, i figure perhaps, its just me that doesnt know how to use it?

---

### Post by cytg on 2007-10-20
details

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


/etc/network/interfaces

auto lo
iface lo inet loopback

---

### Post by cytg on 2007-10-20
haha got it .. restricted driver :))) ..

this **** actually do work out of the box ... go gutsy :)

---

### Post by Dellfan on 2007-10-20
To list networks potentially in range (note you can "see" networks that are marginal enough that you cannot establish a solid connection to) just issue the command:

```

sudo iwlist eth1 scanning

```

or whichever interface is your wireless. Use iwconfig to figure out which is your wireless interface.

An easy way to prod your wirless card after a suspend, if network manager gets confused is to create a script, like:

> #!/bin/bash
# wireless.sh
# Reconnects wireless
# Assumes open network with DHCP running

echo ""
echo "Setting up eth1.... "
echo ""

if [ "$1" = "" ]; then
        # Your wireless network goes here
        sudo iwconfig eth1 essid "your_wireless_network"
        sudo dhclient3 eth1
        exit 0               
        fi
sudo iwconfig eth1 essid "$1"
sudo dhclient3 eth1

Create it, changing the interface and network name as appropriate, make it executable 
and you have an easy way to attach to any wireless network.

"wireless.sh" will reconnect to your network
"wireless.sh some_other_network" will conect to that network

---

### Post by Y2J on 2007-10-21
I am using Latitude D620 and My wireless didn't enabled until I enable it form the restricted drivers. Now it can see the Access points on my office but when I provide the key it's still unable to connect. I hope you can help on this ?

My System is Ubuntu 7.10 Gusty Gibbon (Final), Dell Latitude D620
Wireless Name as appeared under Windows' Device Manager: Dell Wireless 1390 WLAN Mini-Card.
Thank you in advance.

---

### Post by bluedragon436 on 2007-10-21
I have a D610 and dind't have an issue with my wireless card working out of the box, but I do have an issue with once I connect to a wireless network the connection fluctuates, and I am not able to really use the connection.

---

