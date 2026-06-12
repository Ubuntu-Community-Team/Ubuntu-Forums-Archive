---
title: "Getting Wireless to work on a Vostro 1400"
date: 2008-10-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by hkphooey on 2008-10-14
Before I bought this Vostro I did some research around the internet and found a bunch of happy Vostro 1400 Ubuntu 8.04 users. However it seems that the hardware specs between Vostro 1400s vary depending on where and when they're manufactured, so I think that research might have been misleading. 

Anyway, I've been trying to get wireless working on and off for the last 3 or 4 weeks, and I'm almost there, so I thought I'd share my experiences.

First of all, the chipset on this Vostro 1400: 
```
lshw -C network
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0c:00.0
                logical name: eth1
                version: 01
                serial: 00:22:5f:15:7c:92
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless

lspci 
<snip>
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

```
OK, so out of the box, the wireless wouldn't connect to anything. The first thing I tried was enabling the Restricted Drivers. It seemed to like this, and used the wl driver, but wouldn't connect to any networks. I tried an Open AP and also my one running WPA2 Personal. No luck. 

I've been through this with 3 or 4 other laptops so I knew I was in for some fiddling. I located a guide on How to Set up Broadcom chips and started running through few options. 

 - I tried the b43-fwcutter tool, downloading drivers from 3 different locations. None of these worked with ndiswrapper

 - I tried the drivers from the Vista driver disk, taking care to select the ones for XP rather than Vista, which I was aware wouldn't work. No luck. 

 - I downloaded and compiled the latest version of ndiswrapper, and tried that with two or three of the drivers I'd downloaded. No dice. 

At this point, having spent most of a day on this, I decided to leave the machine working off a wired connection, and went about installing the other things I need on it. A few days later I tried again from the top. 

This time it connected OK to an Open AP using the restricted wl drivers. I don't know if my changes the previous time had persuaded it to do this. Anyway I was glad for the small advance. I re-configured my AP for WEP and it would connect to this. All right ... 

But still no WPA2. I started to trace this problem. It seems that the encryption key was accepted OK, but when it went to get an IP address, the dhclient app was unable to sense a reply. It would de-activate the wired connection (eth0), set the AP to my AP, send the encryption key which was accepted and then completely fail to get an IP address. This is an example from my syslog. 

```
Sep 24 13:25:23  NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction. 
Sep 24 13:25:23  NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete. 
Sep 24 13:25:23  NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface eth1 
Sep 24 13:25:24  NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface eth1 
Sep 24 13:25:25  kernel: [   88.025821] eth1: no IPv6 routers present
Sep 24 13:25:27  dhclient: DHCPREQUEST of 192.168.1.100 on eth1 to 255.255.255.255 port 67
Sep 24 13:25:34  dhclient: DHCPREQUEST of 192.168.1.100 on eth1 to 255.255.255.255 port 67
Sep 24 13:25:43  dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
Sep 24 13:25:47  dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Sep 24 13:25:57  dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
Sep 24 13:26:13  dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
Sep 24 13:26:14  dhclient: No DHCPOFFERS received.
```
After this it tried a fallback static IP address and then switched back to the wired eth1. I tried this a few more times, and tried a static IP which also wasn't accepted. OK, well I thought I'd stick with WEP for now. 

Today I had some slack time at work, so I thought I'd try again. I'd read about problems with NetworkManager and WPA2 and DHCP, so I thought I'd try a different NetworkManager. I installed wicd using the instructions on the website, and rebooted. 

The same thing happened again. I could connect via WEP, but not by WPA2. So it seemed to be a problem with this driver and wpa_supplicant. On a whim I started fiddling with the settings on my wireless router. The security was set as follows
Security mode: WPA2 Personal
WPA Algorithms: TKIP
WPA Shared Key: xxxxxxxxxxxxxxxxxxx
Key Renewal Interval: 3600

I changed TKIP to AES, and connected first time. I'm not sure if its the combination of wicd and AES, or whether this will work with NetworkManager as well, but I don't particularly want to change it right now. 

I'm happy for now, but would still like this to be fixed, as I won't always have control over the encryption algorithm of the network I'm connecting to. Hopefully the detail above helps someone else out, and also attracts the attention of developers troubleshooting this problem.

---

### Post by johnshentiro1 on 2008-10-31
I have the same problem with you,can you say more details about where to set these?thanks

---

### Post by hkphooey on 2008-10-31
How far did you get? Does your laptop connect to an open Access Point? A WEP Access Point? 

If its connecting to these (and honestly I tried so many things I'm not really sure what actually got me this far), and you're having trouble with connecting to WPA, then you need to change the encryption settings on the Access Point. 

This is fine if you've got control of your access point, but if its a public one, then you really can't control it, and I don't know what you might try here. This is one reason why I'm particularly keen to get this sorted out.

---

### Post by hkphooey on 2009-05-21
Update: A fresh install of Jaunty 9.04 to a Dell Vostro 1400 works perfectly.

---

