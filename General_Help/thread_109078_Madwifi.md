---
title: "Madwifi"
date: 2005-12-27
forum: General Help
---

### Post by digitalkarabao on 2005-12-27
Question: How would I know (aside from trying to connect to a wireless network which I do not have) if madwifi is properly installed and working in my ubuntu machine?

---

### Post by Lambert on 2005-12-27
madwifi is in the linux-restricted-modules package so if that's installed then madwifi is. run these commands from terminal

```
sudo dpkg -s linux-restricted-modules-`uname -r`
```

this tells you status of the package.

If it is installed, with the card plugged in you can 

iwconfig

if you see your card with ath0 iface being reported then driver is functional.

---

### Post by digitalkarabao on 2005-12-28
thank you sir lambert.

i ran iwconfig and got the following output:

lo        no wireless extensions.

eth0      no wireless extensions.

ath0      IEEE 802.11  ESSID:""
          Mode:Managed  Frequency:5.8 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:6 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

ppp0      no wireless extensions.

does this mean the wifi capabilities in my ubuntu machine is enabled? if so, how do i connect to an open hotspot. i am using wifi-radar. how do i configure it to connect to an open hotspot? thanks for the help.

---

### Post by zoiks on 2005-12-28
Yes, your madwifi seems to be installed properly.

If you know the ssid of the hotspot,

[COLOR="Red"]sudo iwconfig ath0 essid <ssidname>[/COLOR]

should do the trick.  At that point, two LEDs should light up on your card (if it's a cardbus card).  You might have to restart dhcp with something like

[COLOR="Red"]sudo dhclient ath0[/COLOR]

to get a new ip address and new dns information.  I don't know wifi-radar, but basically to connect to a public hotspot, just set the ssid name and make sure dhcp knows to check for new info.

---

