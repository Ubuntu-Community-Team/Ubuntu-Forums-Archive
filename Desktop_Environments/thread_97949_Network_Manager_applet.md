---
title: "Network Manager applet"
date: 2005-12-02
forum: Desktop Environments
---

### Post by Dr. Nick on 2005-12-02
I have a wireless card with a prism2 chipset and am using the wlan-ng drivers. The connection works it just has to be maunally started. I am trying to make it easier to switch hotspots so I installed the nm_applet.

Only prboblem is it doesnt see my wireless card so no scanning or anything .I keep getting this error when working in a console which I think is related I just dont know how to fix it and havent seen it mentioned.

```
NetrworkManager: <WARNING>     (): nm_device_set_mode  (wlan0): error setting card to Infrastructure mode. errno = 95
```

If I look under the network control panel in gnome it says its a wireless device called wlan0, but when connected and I hit properties on the 2 monitor icon it says the type = ethernet. shouldnt that say wireless? I am thinking I may need to set the mode here?

here is my interfaces file
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
#       map eth0
map wlan0
# The primary network interface
iface wlan0 inet static

wireless-essid xxxxxxxx
wireless-key xxxxxxxxxxxxxxxxxx
wireless_enc on
wlan_ng_key0 xxxxxxxxxxx
address 10.10.124.101
netmask 255.255.255.128
gateway 10.10.124.4

auto wlan0



#iface wlan0 inet dhcp





```

---

