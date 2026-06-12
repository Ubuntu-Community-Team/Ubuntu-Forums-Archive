---
title: "WPA still not working"
date: 2005-10-27
forum: Desktop Environments
---

### Post by dizbah on 2005-10-27
I am having an extremely difficult time getting WPA to work with Ubuntu.  When doing the following:

sudo ifconfig wlan0 up && /usr/sbin/wpa_supplicant -w -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf -dd
 
I get  Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapper'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
Failed to read configuration file '/etc/wpa_supplicant.conf


I have my drivers loaded, double checked my password in the netgear router that I have.  All is failing.  My config file looks like this:
network={
ssid="network name"
#psk="password"        
psk=f64efb43fd923532d53f084c9027ac5d0d4a9642cfaa0109802d5d2706c583bf
key_mgmt=WPA-PSK
proto=WPA
}

Really need to get this solved.  Please help!

---

