---
title: "Weird ata1 error from command-line"
date: 2009-06-18
forum: General Help
---

### Post by quazi on 2009-06-18
Ubuntu seems to boot up perfectly fine and from within Gnome, everything is hunky dory.

However, whenever I shutdown or hibernate it takes a long time (and hibernation sometimes fails).  Meanwhile, the terminal repeatedly spits out
```

ata1: irq_stat 0x0000040, connection status changed
ata1: SError: { Dev Exch }
ata1: exception Emask 0x10 SAct 0x0 SErr 0x4000000 action 0xe frozen

```

If I hit Ctrl+Alt+F1 during regular usage, I see the same message repeated over and over.

Any ideas?

---

### Post by quazi on 2009-06-18
Well, I think this might be a clue:

[https://bugs.launchpad.net/ubuntu/+bug/198871](https://bugs.launchpad.net/ubuntu/+bug/198871)

I have a JMicron IDE controller on my ASUS motherboard and, unfortunately, a DVD drive attached to it.

---

