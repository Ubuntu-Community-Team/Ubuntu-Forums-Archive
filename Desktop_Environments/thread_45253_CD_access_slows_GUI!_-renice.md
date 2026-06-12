---
title: "CD access slows GUI! -renice?"
date: 2005-06-29
forum: Desktop Environments
---

### Post by jago25_98 on 2005-06-29
Lots of things seem to slow the mouse and GUI down.
For example, these include:

- copying something off a CD and onto the destop
- running DC++ for linux while it's `hashing` files; a CPU intensive thing. I reniced this program to 16 and it still took 50% of the CPU

If I renice X to -1? This doesn't help? Is it even relevent?

---

### Post by Takis on 2005-06-30
Have you enabled DMA for your device?

```
$ sudo hdparm -d1 /dev/cdrom
```

And then give it a go. If that works, you'll need to enable it every time you boot:
[http://ubuntuforums.org/showthread.php?t=30949](http://ubuntuforums.org/showthread.php?t=30949)

---

