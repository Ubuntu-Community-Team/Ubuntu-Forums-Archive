---
title: "ssh then VPN"
date: 2016-11-06
forum: Desktop Environments
---

### Post by Geoff_Lane on 2016-11-06
Folks,

I manage a friend's computer (Ubuntu 14.04) remotely using ssh and shared key login. I have 16.04

If whilst connected using SSH I then use command line on the remote computer to connect to an openVPN server will my SSH drop?

I appreciate a shut down and restart would resolve it anyway.

The only reason for the OpenVPN connection is we are in different Countries and the VPN can resolve some connection issues.

Geffers.

---

### Post by papibe on 2016-11-06
Hi Geoff_Lane.

No it shouldn't drop just because you open the VPN connection (they use different ports).

However, your ssh connection may slow down if you transfer lots of data over the VPN connection, and even time out. if you get closer to your friend's bandwidth limit for a certain period of time.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Geoff_Lane on 2016-11-19
> **papibe said:**
> Hi Geoff_Lane.

No it shouldn't drop just because you open the VPN connection (they use different ports).

However, your ssh connection may slow down if you transfer lots of data over the VPN connection, and even time out. if you get closer to your friend's bandwidth limit for a certain period of time.

Hope it helps. Let us know how it goes.
Regards.

I used torvpn - worked well whilst in US and actually at the computer in question but when I returned to UK and made ssh connection to the computer and via remote computer's terminal connected to torvmp using an openvpn setup.

My ssh connection then froze and I had to log on to the torvpn web page control panel page and cancel the connection before I could reconnect to ssh

Reading up on the torvpn help pages there is a way to connect but I haven't bothered to try as yet as the VPN from the States was only to access the British BBC web site.

Geffers

---

