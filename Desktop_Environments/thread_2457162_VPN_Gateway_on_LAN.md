---
title: "VPN Gateway on LAN"
date: 2021-01-27
forum: Desktop Environments
---

### Post by Geoff_Lane on 2021-01-27
Folks, I've  run openVPN on Ubuntu and Android devices but am wondering how I might route a smart speaker device through a VPN.

The objective is merely to try and get a US radio station to stream my location in UK.

I have seen some suggestions using Raspberry Pi devices as a gateway but this then requires the client device to be able to alter its gateway address, which I don't think you can do with smart speakers.

Any suggestions appreciated. 

Geoff

---

### Post by TheFu on 2021-01-27
Any device using DHCP can be provided with a different gateway if your router or DHCP server supports that.  I know opnsense does - each DHCP reservation can specify a different gateway if needed.  I doubt typical $50-$200 home routers support that feature.  You could force all clients that use DHCP to go through the VPN, however.

Or you could disable DHCP in the router and run a separate DHCP server on your Linux systems. These certainly can set the gateway for each DHCP client individually, assuming you don't want to  or cannot replace the router.

---

### Post by Geoff_Lane on 2021-01-28
> **TheFu said:**
> Any device using DHCP can be provided with a different gateway if your router or DHCP server supports that.  I know opnsense does - each DHCP reservation can specify a different gateway if needed.  I doubt typical $50-$200 home routers support that feature.  You could force all clients that use DHCP to go through the VPN, however.

Or you could disable DHCP in the router and run a separate DHCP server on your Linux systems. These certainly can set the gateway for each DHCP client individually, assuming you don't want to  or cannot replace the router.

Thank you for quick response.

My router, although a cheap TP-Link device does allow quite a bit of configuration but much of it is beyond me but your suggestions re DHCP have given me an idea.

The Raspberry Pi device can be set up as a Router Access Point (I have tried this), it issues a completely different subnet range and data is transferred via 'bridging' interfaces eth0 and wlan0.  I shall try this, install openVPN and see if that is an option, appreciate the virtual TAP/TUN adapter might have to join the 'bridge' f this is possible but shall give it a try.

Geoff

---

