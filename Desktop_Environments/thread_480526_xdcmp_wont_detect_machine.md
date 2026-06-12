---
title: "xdcmp wont detect machine"
date: 2007-06-21
forum: Desktop Environments
---

### Post by panchopc on 2007-06-21
hi guys,
im tryint to acces an ubuntu server via xdcmp
i have to networks at my company

10.1.x.x
and
10.4.x.x

i have a workign xdcmp on 10.1.1.10 and can access it with andy 10.1.x.x computer
and it does ping any computer with 10.4.x.x thing is when i try to login via xdcmp from a 10.4.x.x the computer doesnt apear any ideas?

---

### Post by AlanSmithee on 2007-08-05
> **panchopc said:**
> hi guys,
im tryint to acces an ubuntu server via xdcmp
i have to networks at my company

10.1.x.x
and
10.4.x.x

i have a workign xdcmp on 10.1.1.10 and can access it with andy 10.1.x.x computer
and it does ping any computer with 10.4.x.x thing is when i try to login via xdcmp from a 10.4.x.x the computer doesnt apear any ideas?

(I'm guessing you mean XDMCP, no xdcmp.)  I'm not an expert on this protocol, but I suspect that the router on the 10.1.0.0/16 network is somehow stopping the XDMCP traffic.  A quick look at XDMCP on Wikipedia suggests this might be because the router is blocking UDP port 177 traffic (a bit unlikely on an office LAN) or perhaps the host with the display manager on the 10.1.0.0/16 network is using 'BroadcastQuery', which almost certainly *will not* make it through the router.

---

