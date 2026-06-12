---
title: "Wired and wireless at the same time?"
date: 2009-05-01
forum: General Help
---

### Post by Rackstar on 2009-05-01
Hi,

Every time I reboot my ubuntu it connects to the net through eth0, like it should. But why is it always connecting through wireless also?

Are there advantages when having 2 connections? Or do they just cancel each other out?

I find myself always disabling my wireless when the cable is plugged in, but I don't really know for sure if this is necessary?

Thanks!

---

### Post by dandnsmith on 2009-05-01
It's connecting thru both because that's what it has been instructed to do.

The routing will be set to use one or the other (possibly the first to connect?), and all the traffic will follow that route unless you convince it otherwise.

I wouldn't put turning off the wireless as a high priority thing to do, but could save battery time for a laptop.

---

### Post by Rackstar on 2009-05-01
Thanks for your reply, this cleared things up for me.

But this is potentially a little confusing towards users. Maybe it would be better to only auto-connect to wireless when wired is unplugged.

---

### Post by NilsE on 2009-05-01
I have never seen any OS do that and don't think it is supposed to.  When I plug in the cable it always wins and I get the wired connected icon and if the cable is not in I get wireless connected.  I see no indication that both are ever active.

That may actually be a bug so I would open a bug report and see what response you get.

---

### Post by Rackstar on 2009-05-01
I added this to a bugreport of network-manager I did yesterday, I have been experiencing other strange behaviour, maybe they are connected.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/370274](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/370274)

---

