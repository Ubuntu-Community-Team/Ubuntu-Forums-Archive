---
title: "VPN to Win SBS 2003 using local Gateway"
date: 2009-06-22
forum: General Help
---

### Post by jamesisin on 2009-06-22
In the wacky world of Windows, using the local gateway (ignoring the VPN gateway) while connected to a VPN is a simple matter of ticking one check box.  I need to make my Ubuntu machine behave in the same manner, but I can't see how that is to be done within the VPN client.

I'm using 8.10 with the built in VPN client (with the PPTP plugin installed, of course).

Can someone please tell me how to set this up on my Ubuntu machine?

---

### Post by jamesisin on 2009-06-22
Well, on XP it's as easy as ticking a check box.  [s]On Vista I am also unclear how to make that happen.[/s]

But I certainly need to make this function on my Ubuntu desktop so that I can better provide support for my clients who use Windows networks.

Can anyone tell me how to default the VPN traffic to my local network instead of through the tunnel (I'm thinking of things like my browser, my chat client, and so forth)?

EDIT:

I found the Vista check box.  They have rather buried it.

1. Find the VPN in question and pull up its Properties diaglog
2. On the Networking tab choose IPv4 or IPv6 and click the Properties button
3. Click on the Advanced button on the IPv4/6 dialog
4. Uncheck "Use default gateway on remote network"

(But I want to use my Ubu machine....)

---

### Post by jonobr on 2009-06-22
Hello

I use kvpnc which uses vpnc and I am connecting to a firewall using a cisco pcf file and ipsec security.

My normal default action is to use the regular gateway on my wired connection and when I need to do some remote administration of a firewalled site I kick off my kvpnc.

This is a private network and not a complicated one, so all my regular network traffic is routed to the real world, whereas my traffic for this other network is routed correctly to this other firewalled address using the vpn I created.

Looking at the kvpnc settings, I do notice a general setting for routes, that says by default, replace default route,
this can be dropped down to keep default route.

See attached screenshot.
Im not sure if this helps? With a specific question like this Im thinking there would not have been a lot of responses

Cheers

---

### Post by jamesisin on 2009-06-22
> **jonobr said:**
> Hello

I use kvpnc which uses vpnc....

Thanks.  I am not using kvpnc so things do look a bit different.

I am using the regular Network Connections utility (typically seen in the notification area) and the PPTP plugin for attaching to Windows.

There is a setting called "Ignore automatically obtained routes" but it doesn't seem to do anything.

---

### Post by jonobr on 2009-06-22
Sorry bout that, I have set my network to unmanaged so I dont deal with the network connection utility, I found it funky in Jaunty, although it may be fixed by now.

---

### Post by jamesisin on 2009-06-22
Anybody else care to take a crack at it?

---

### Post by jamesisin on 2009-06-26
Bueller?

---

### Post by jamesisin on 2010-01-23
The solution (more or less):

[http://www.soundunreason.com/InkWell/?p=1234](http://www.soundunreason.com/InkWell/?p=1234)

---

