---
title: "Need help with ipx-support for starcraft"
date: 2007-06-10
forum: Gaming &amp; Leisure
---

### Post by piratenaapje on 2007-06-10
I just recently discovered starcraft. After playing this for a while in singleplayer mode, I felt the urge to play this over lan. Too bad that I can't seem to get ipx to work under linux.

I changed a bit in my /etc/ipx.conf file, it now looks like this:

```


# this attempts auto-configuration
IPX_AUTO_PRIMARY=off
IPX_AUTO_INTERFACE=yes
IPX_CONFIGURED=yes
# for manual configuration, set IPX_CONFIGURED=yes,
# and set the options below for your system
IPX_DEVICE=eth1
IPX_FRAME=802.2        # either 802.2, 802.3 or EtherII
IPX_INTERNAL_NET=no
IPX_NETNUM=836fc800            # your internal network number
# routing options
IPX_SERVER_ROUTE=yes    # setup route to external server?
IPX_SERVER_NETNUM=836fc800        # your server's internal network number
IPX_SERVER_NODENUM=0018DE488442        # your server's node number

```

After doing this change, I can see, after I use the command "ifconfig eth1", this:
IPX/Ethernet 802.2 addr:836FC800:0018DE488442
it wasn't there before my changes

After starting starcraft and trying to play a game using the ipx-protocol, I still get the same error:
 "unable to initialize network provider"

If you know a solution to this, don't hesitate to help.

Edit: found the solution, all I needed to do was run starcraft as root with this ipx.conf

---

### Post by dfreer on 2007-06-10
ummm. a better idea than running ipx is to install the latest update for starcraft (I think they are at 1.14 now), because it supports TCP/IP and there is no need to mess with IPX

---

