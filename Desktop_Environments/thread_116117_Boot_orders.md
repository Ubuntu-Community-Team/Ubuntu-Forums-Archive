---
title: "Boot orders"
date: 2006-01-12
forum: Desktop Environments
---

### Post by JammingJames on 2006-01-12
Is there any way to disable ubuntu from "configuring network adapters" untill ubuntu is fully booted.  Basically when I start the system, it pauses at that point for several minutes every time I boot and then just fails.. Yet, im always able to get on the internet wirelessly.. Can I just have it not do that one procedure?  Thanks james.

---

### Post by r4ik on 2006-01-12
Unplug or switch of the device during boot ?
Must be a better way agreed but if it isnt there it cant be detected :)
Have a look at System-settings(second one from the top)-network.
Dunno if it is called settings bad English sorry.
Had a cup a coffee, turn it of on shutdown is what i wanted to say.
This post a mess? Nah could be wourse.

---

### Post by schilcha on 2006-01-12
Had a similar problem, though can't tell if it really fits your situation.

Anyways: I had this long pause when booting my notebook with no network-cable plugged in. This came from the system waiting for the dhcp server until it gives up after a or the other minute.

What one can do quickly is pressing CTRL+C during "configuring network adapters".

Another thing I've heard of (but not tried yet) is installing ifplugd. Telling from the package description, the interface is configured as the cable is plugged in.

The last and probably hardest way is to recompile a modified version of ifup. That's the way I did it. Requesting a dhcp-lease is done in the background while booting continues normally. (If I had known ifplugd back then, I would have given it a try)

Good Luck anyways

---

