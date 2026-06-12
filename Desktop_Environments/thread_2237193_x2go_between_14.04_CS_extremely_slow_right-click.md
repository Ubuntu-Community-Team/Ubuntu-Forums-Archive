---
title: "x2go between 14.04 C/S extremely slow right-click"
date: 2014-07-31
forum: Desktop Environments
---

### Post by TheFu on 2014-07-31
Both the client and server are 14.04 running current x2go.  Everything is working great, except right clicks are massively delayed - like 20-40 seconds.  Also see the same behavior from a 14.04 client and 12.04 server.

Left-clicks work as expected.
Center-clicks work well.
Audio works as expected (really excellent).
Video playback works better than anything else I've seen (freenx, etc), but the right click is delayed terribly.

I've tried changing the image compression and have tested it on a local GigE network and from remote DSL-like locations.

Also tried from a Windows client - same behavior.  Seems to be the x2go server.
Since it is a remote desktop, using LXDE to limit the "GUI Cheese".  Outside the right-click delays, it is working fantastic.
[B]
If you use x2go and the right-clicking works fine, please respond.[/B] At least then I'd know it is my issue.

Ideas?

---

### Post by andrew-drup on 2014-08-25
I'm having exacty the same problem on 14.04

---

### Post by TheFu on 2014-08-25
Get the latest client for Windows (August 2014 sometime) ... that and setting the resolution properly made the problem go away. The Linux repo client and server have updated ssh libraries which correct the issue.

Oh - and disable the client-side file sharing to resolve the high-CPU every 2 seconds issue on the server-side.  My server-side is a VM and the CPU spikes were negatively impacting other VMs.

Even extending the display across dual monitors is working perfectly here now - though I don't run that way normally.

Working really well here now.

---

