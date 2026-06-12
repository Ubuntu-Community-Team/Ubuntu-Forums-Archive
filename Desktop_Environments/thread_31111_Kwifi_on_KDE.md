---
title: "Kwifi on KDE"
date: 2005-05-01
forum: Desktop Environments
---

### Post by trivialpackets on 2005-05-01
Hey all.  I've been up and using Kubuntu for a few weeks now, and using Ubuntu since October, but am having issues with Kwifimanager.  I cannot switch to a different network.  Not sure what's going on, or if I just don't understand the KWIFI.  But if I got to Gnome, goto network settings and change it there I can then login to KDE without issue, or when I'm just at home, and have been logged into my home network before, everything is fine.  So I'd like to be just using one, and am pretty satisfied with KDE, any advice on how to fix this issue?

---

### Post by epb613 on 2005-05-02
I´ll second your problem. KWifiManager has been completly useless for me when it comes to switching or logging on to wifi networks. What I have been doing is just setting up the networks by hand (basically just making the changes that kwifimanager would have made itself).

To do so:

First type iwconfig to find out the name of your wireless device (usuall eth1 or wlan0). Let´s pretend it´s eth1.

Now edit /etc/network/interfaces and add the following two lines at the end of the file:
iface eth1 inet dhcp
auto eth1

If you´re using WEP, then in between those two lines add these two lines:
wireless-essid yourwirelessessid
wireless-key Y0URW1R3L355K3Y

Save the file and reboot (make sure the wirless is the only active connection - unplug any other network cables from the computer).

---

