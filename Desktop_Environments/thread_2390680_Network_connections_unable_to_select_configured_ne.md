---
title: "Network connections unable to select configured network in 18.04"
date: 2018-05-01
forum: Desktop Environments
---

### Post by egandt on 2018-05-01
I need to connect to a cicso vpn for work, I created the connection by right clicking on "Networks" and select "configure network connections" all goes well I can set up the connection./  However I'm unable to actually select the connection in the list to start it.

I do not know what else to say I'd assumed it would appear as it should on the list so that I can trigger it to connect, but instead the list remains empty and I'm unable to get the VPN to activate.

This seems like a very simply thing, but it says never used (which it is not as I can not trigger it), I'd expected it to show in teh list when I click on teh icon so that I can select and execute it.

Once created I can "delete or export" but never run!


EDIT: in XFCE, which I installed just to try to connect, I can see the connections (so that is an improvement), but they are grayed out and can not be clicked on to start.  I do not see why networking on Linux is always so very painful.

I'm assuming this has something to do with using netplan and not /etc/network/interfaces, but beyond that and lacking any documentation or errors I'm stuck.

What am I doing wrong?
ERIC

---

### Post by egandt on 2018-05-01
The trick is to simple replace: 01-netcfg.yaml

mv /etc/netplan/01-netcfg.yaml /etc/netplan/01-netcfg.yaml.org
echo "# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: NetworkManager
" >> /etc/netplan/01-netcfg.yaml

and reboot, network manager is now functional.

---

