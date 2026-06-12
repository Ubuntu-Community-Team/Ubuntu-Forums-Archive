---
title: "Does Jaunty Server support Intel?"
date: 2009-06-12
forum: General Help
---

### Post by InvisibleMan on 2009-06-12
Specifically the Intel Pro/100 VE.

I would have thought so, but I'm having huge difficulty making this work. My would-be server can pick up a DHCP IP, an IP based on the MAC, or an IP hard wired into the config files. However, the process goes something like this:

Server: Broadcast to network for IP
Network: Lease offered
Server: <nothing>

Server: Broadcast to network for IP
Network: Lease offered
Server: <nothing>

Repeat indefinitely.

For static lease DHCP configurations, ifconfig shows no assigned IP address, even though the network monitoring software elsewhere shows the MAC matched up with the assigned IP and traffic from the server.

This system has successfully used Desktop 8.04, Desktop 8.10, the LiveCD for Desktop 8.04, the LiveCD for Desktop 8.10, FedoraCore, XP Pro and Vista. The LiveCD for 9.04 Desktop gives me a similar problem as the server installation.


Yes, I have downloaded the driver from Intel.
Yes, I have checked the hardware.
Yes, I have manipulated every networking file I can think of.

This is very frustrating. It is not making it easy for me to advocate Ubuntu as our company network's OS of choice.

---

### Post by el.otro on 2009-06-12
you should consider posting this question on the "Server Platforms" section, or the "Networking and Wireless", it seems there are no answers around here...

However, I googled "intel pro 100 ve ubuntu support" and it seems the card has worked for someone (2006) and then someone complained about it not working (2007), so I wouldn't know what to tell you...  If you said it worked on Fedora, and you looked up the drivers, etc, etc, I would say the only option is to change it to the networking section, someone might have experience w/it.

:(

---

