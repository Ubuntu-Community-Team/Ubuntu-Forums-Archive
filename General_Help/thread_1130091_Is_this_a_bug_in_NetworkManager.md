---
title: "Is this a bug in NetworkManager?"
date: 2009-04-19
forum: General Help
---

### Post by edieguez on 2009-04-19
For several days I've been struggling to understand why my local network would slow down to 5kb/s when transferring files across machines over 802.11g but would get 1mb/s when transferring files across the internet. I discovered that deactivating NetworkManager at boot - by renaming S28NetworkManager to K72NetworkManager in all the rcX.d directories - and turning on my wireless connection manually through rc.local, results in sustained transfer speeds of 1mb/s - 2mb/s as I would expect. I am running Ubuntu 8.10 with all the latest updates on all my machines - this is one desktop, and two eeePCs running EasyPeasy 1.0 (Ubuntu 8.10) - with one of the eeePCs functioning as a fileserver. This is what my rc.local does:

ifconfig eth0 down
dhclient -r wlan0
ifconfig eth0 up

ifconfig wlan0 down
dhclient -r wlan0
ifconfig wlan0 up
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -B
dhclient wlan0
ifconfig wlan0 mtu 1492
iwconfig wlan0 rate 54M

and here is my wpa_supplicant.conf

ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="MyNetwork"
        proto=WPA
        key_mgmt=WPA-PSK
        psk="MyKey"
        pairwise=TKIP
        group=TKIP
}

My router is running the opensource firmware Tomato 1.23 with fairly normal options. Strangely enough, this appears to only happen if my desktop uses NetworkManager versus my manual commands. That is, one of the eeePCs (901) is using NetworkManager and no slowdown is seen when transferring with that machine. Though the fileserver (also an eeePC - 900HA) is wired to the wireless router because its wifi chip is a bit flaky with Ubuntu at the moment. 

If anyone else has seen the same behavior, please let me know.

---

