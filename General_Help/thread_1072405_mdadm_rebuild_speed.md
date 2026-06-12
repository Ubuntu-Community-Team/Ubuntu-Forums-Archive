---
title: "mdadm rebuild speed"
date: 2009-02-17
forum: General Help
---

### Post by xxsludgexx on 2009-02-17
Is there a way to set up software raid so that it favors faster rebuilds over disk io, or the other way around?

Lets say I have a 4 disk, raid 5 setup.
I am constantly writing data to these disks.
One drive fails, the data writing continues.
I replace the drive, data writing continues, but the rebuild doesn't seem to start until I stop writing data.

I'd like to configure it such that the writes slow down, and the rebuild starts right away. Any tips?

Too much to ask for software raid? ;)

Edit: I have found /proc/sys/dev/raid/speed_limit_min and /proc/sys/dev/raid/speed_limit_max
I will play with these, but would still like an answer.

---

### Post by xxsludgexx on 2009-02-24
bump

---

### Post by fjgaude on 2009-02-24
I know of no way... that's the price we pay for relative slow but huge drives. Things were different just three yars ago wherein 32G was a big drive. I/O speed is always an issue with huge drives and multitasking...

---

