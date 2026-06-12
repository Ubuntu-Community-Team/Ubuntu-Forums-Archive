---
title: "VPN Cisco connection failed"
date: 2009-04-22
forum: General Help
---

### Post by frecon on 2009-04-22
I'm trying to connect to a cisco VPN but with no success. I'm using the network-manager together with network-manager-vpnc to connect. Any ideas why I can't connect?

OS: Ubuntu 8.10

/var/log/daemon.log
```
Apr 22 16:09:21 frecon-desktop NetworkManager: <info>  Starting VPN service 'org.freedesktop.NetworkManager.vpnc'... 
Apr 22 16:09:21 frecon-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' started (org.freedesktop.NetworkManager.vpnc), PID 24009 
Apr 22 16:09:21 frecon-desktop NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.vpnc' just appeared, activating connections 
Apr 22 16:09:21 frecon-desktop NetworkManager: <info>  VPN plugin state changed: 1 
Apr 22 16:09:21 frecon-desktop NetworkManager: <info>  VPN plugin state changed: 3 
Apr 22 16:09:21 frecon-desktop NetworkManager: <info>  VPN connection 'VPN-Connection' (Connect) reply received. 
Apr 22 16:09:21 frecon-desktop NetworkManager: <info>  VPN plugin failed: 1 
Apr 22 16:09:21 frecon-desktop NetworkManager: <info>  VPN plugin state changed: 6 
Apr 22 16:09:21 frecon-desktop NetworkManager: <info>  VPN plugin state change reason: 0 
Apr 22 16:09:21 frecon-desktop NetworkManager: <WARN>  connection_state_changed(): Could not process the request because no VPN connection was active. 
Apr 22 16:09:21 frecon-desktop NetworkManager: <info>  (eth0): writing resolv.conf to /sbin/resolvconf 
Apr 22 16:09:21 frecon-desktop NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
```

---

### Post by mwacky on 2009-04-22
Have you connected with other pc's on your network?  It could be a blocked port by your ISP or Router, not network-manager.

---

### Post by frecon on 2009-04-22
> **mwacky said:**
> Have you connected with other pc's on your network?  It could be a blocked port by your ISP or Router, not network-manager.

The VPN works in Vista (I have a dual boot). I can connect to other pcs on the network and share files. So I guess that mean I'm not blocked.

Is there anything I can try?

---

### Post by mwacky on 2009-04-23
It could be worth a try with PPTP:

[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

It's been a while but we had a cisco firewall but we used PPTP to connect to it, i guess it depends on the vpn server setup.

Sorry I can't be more help.

---

### Post by frecon on 2009-04-25
> **mwacky said:**
> It could be worth a try with PPTP:

[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

It's been a while but we had a cisco firewall but we used PPTP to connect to it, i guess it depends on the vpn server setup.

Sorry I can't be more help.
Thanks for your tip but unfortunately it didn't work. 

Is there something else I can do? I'm starting to get frustrated over this problem since I can't work from home without the vpn tunnel.

---

### Post by imageek on 2009-04-27
I am having the same problem. I can manually connect just fine using vpnc from the command line, but i would like to have NetworkManager control this so i can have one place i need to go to instead of many. Any help would be appreciated and i would be willing to do any testing that someone might suggest.

---

### Post by frecon on 2009-04-30
I got it to work from terminal now. The problem was that I needed to enter the correct domain. Got it from the vpn provider and it works fine now from terminal with ```
sudo vpnc-connect myvpn
``` where myvpn is the name of the file i created in /etc/vpnc/myvpn.conf

It looks like this ```
IPSec gateway 127.0.0.1
IPSec ID group_username
IPSec secret group_password
Xauth username username
Xauth password password
```
Change the last word on each line to your info.

But, I still doesn't work to connect to cisco vpn from networkmanager (nm-applet). I can connect but when it connects to the vpn, the lan goes automatically offline. It seems I can't have them both on at the same time. Weird!

---

### Post by shrijith1 on 2011-03-14
I had the same problem...Even though this a 2 year old thread, in case somebody is still facing the issue....Uncheck "Available to all users" and it should work...

---

### Post by CarlGWatts on 2011-06-20
I had the same problem.  If I tried to connect using network-manager the connection would fail.

But if I created my own VPN1.conf file in /etc/vpnc as described above and then used the command

---

### Post by CarlGWatts on 2011-06-20
I had the same problem: if I tried to connect using network-manager then the connection would fail.

But if I created a VPN1.conf file in /etc/vpnc as described above and then used the command:
    sudo vpnc-connect VPN1
then vpn connected successfully...

So the bug has something to do with network-manager or the network-manager GUI for VPN

I am using an up-to-date maverick release

---

