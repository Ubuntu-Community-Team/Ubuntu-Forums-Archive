---
title: "Thunderbird connets through wrong network interface"
date: 2009-04-23
forum: General Help
---

### Post by ike on 2009-04-23
Hi,

A have a problem with Thunderbird in Jaunty. I use a VPN connection to access my customer's servers. With Jaunty I cannot send mail while the VPN connection is active (which worked fine in Intrepid), because the mail server doesn't allow relaying from the IP i get from the VPN service.

Of course, I would rather send mail with my own ip, but I can't find any settings for that in thunderbird.

My network interface is called eth0 (192.168.1.42), and when I am connected to the VPN I get an extra interface called tun0 (10.200.17.15). I want Thunderbird to always use eth0, but the mail server logs says it doesn't allow relaying from my tun0 ip number (which it shouldn't, of course).

---

### Post by Peter09 on 2009-04-23
The VPN connection can be configured to limit all comms to go through the VPN, there are options in the server configuration file for that (OpenVPN). 

Normally your thunderbird application should use your local gateway by default to find a route out to the Internet. It sounds like you are restricting traffic to the VPN gateway only.

---

### Post by Peter09 on 2009-04-23
Note - with your VPN open type

```
route
```

in a terminal to see what routing has been set up.

---

### Post by ike on 2009-04-23
Thanks for the quick reply. (wish I could be just as quick, but today is the Major System Failure Day at the office)

The route is different when I am connected to the VPN. It then goes through my customer's gateway.

I want some of my applications (eclipse, rdesktop) to go through the VPN, but the rest (firefox, thunderbird etc) should go through my own gateway. Is that possible? Is it necessary? :)

I am using network manager to connect to the VPN.

---

### Post by Peter09 on 2009-04-23
This will get very complex because it depends on your routing. It sounds as though the default gateway has been setup as your customers vpn link.

Your options are to explicitly route the applications that you want to use across the network, by pointing them at the machines on the customer site, and / or specifying the default gateway as the local gateway.

---

### Post by ike on 2009-04-23
> **Peter09 said:**
> This will get very complex because it depends on your routing. It sounds as though the default gateway has been setup as your customers vpn link.

Your options are to explicitly route the applications that you want to use across the network, by pointing them at the machines on the customer site, and / or specifying the default gateway as the local gateway.

Specifying the local gateway as the default gateway sounds like a good plan. Does that mean that if I am trying to reach an ip address on my customer's internal network, the traffic will automatically be routed through their gateway, and everything else through my local gateway?
Is that configured on the client or server?

---

### Post by Peter09 on 2009-04-23
As I understand it, you most probably have a route setup which advertises your customer LAN on your network. So your machines know where to go to get to a customer machine. There will also be routes existing on your LAN to allow local machines to find other local machines. 

As long as your local LAN does not have the same IP schema as the Customer LAN all will be well.

The issue is where the  gateway is being advertised. This ip address is where packets are sent for address that do not exist in the routes that are 'known'. You need to advertise the 'local' gateway locally (which should happen). 

There are settings at the server end which overide this and advertise the Customer gateway into the local LAN. This is likely what is happening.

---

### Post by ike on 2009-04-23
Yes, that sounds right. I believe we have had this problem in the past, and our customer is running windows, so eventually they will screw things up, right? ;)

I'll ask the sysadmin to change the setting. Thanks a lot Peter09, you've been a big help! :KS

---

