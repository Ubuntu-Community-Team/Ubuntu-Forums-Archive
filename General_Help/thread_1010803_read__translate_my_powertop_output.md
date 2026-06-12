---
title: "read / translate my powertop output"
date: 2008-12-14
forum: General Help
---

### Post by spandanj on 2008-12-14
hi, 

can someone translate my powertop. what is the 'wake-ups'? is it too high on my laptop?

see attached image.

---

### Post by northern lights on 2008-12-14
Currently the dirty writeback time variable is set to 5 seconds. It would be advisable to extend this time in order to decrease disk activity.
This is both useful for saving energy and extending the harddisk's lifespan.
Run ```
echo 1500 > /proc/sys/dirty_writeback_centisecs
``` to set it to 15 seconds. Adapt 1500 to whatever you prefer, but I'd say this is an okay figure.

If you want in-depth info on the topic, here's a decent article:
[Aggressive Writeback in the Linux Kernel]("http://www.westnet.com/~gsmith/content/linux-pdflush.htm")

---

