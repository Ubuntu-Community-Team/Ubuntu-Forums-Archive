---
title: "Wireless on Dell Lat D410 with Kubuntu 7.10"
date: 2007-12-01
forum: Dell  Ubuntu Support
---

### Post by Chrys6571 on 2007-12-01
Im new to Kubuntu so please bare with me.

I have a Dell Lat d410 that I cannot get the wireless to work with out entering the following commands:

sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>


When I enter all this it works PERFECTLY but once I shut it down or reboot I have to reenter all this again.

I dont think its a driver issue since it works when I enter the commands.
I also edited the alias file to kill off ip6, but no go i then created a bad_list file in the same dir as the alias file and rebooted both times still no go.  Any help would be appreciated.

---

