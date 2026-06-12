---
title: "unwanted process... how do I stop them? (not in BUM)"
date: 2005-07-25
forum: Desktop Environments
---

### Post by spudley on 2005-07-25
I have some unwanted processes running:

evolution-alarm-notify
evolution-data-server-1.2
evolution-exchange-storage

I don't use evolution, and won't until I make a full switch from XP, but in the mean time, really don't want these running taking up resources that I could use elsewhere.

I have the BUM (Boot Up Manager) installed, but nothing appears to be related to the evolution processes found in the System Monitor.

Any advice on the removal of just these processes, while leaving Evolution intact on my system for when I ever decide to use it?

Thanks!

---

### Post by ShaneR on 2005-07-25
Well, I don't know what to do for BUM, but once you're at the desktop you can open up a terminal and :

```
evolution --force-shutdown
``` 

That's what I do...

---

