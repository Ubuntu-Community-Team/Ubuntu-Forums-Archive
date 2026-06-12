---
title: "[SOLVED] No Temperature Sensor for AMD Quad"
date: 2008-12-17
forum: General Help
---

### Post by Michaelg14 on 2008-12-17
I just upgraded my cpu to an AMD 9950 quad core and my temperature sensor for Sensor Applet in my Gnome panel is gone.  My BIOS reports the cpu temp but there is apparently no sensor that the applet recognizes.  It worked fine with an AMD 64 X2 cpu. Anybody have any ideas?

---

### Post by dcstar on 2008-12-17
> **Michaelg14 said:**
> I just upgraded my cpu to an AMD 9950 quad core and my temperature sensor for Sensor Applet in my Gnome panel is gone.  My BIOS reports the cpu temp but there is apparently no sensor that the applet recognizes.  It worked fine with an AMD 64 X2 cpu. Anybody have any ideas?

Have you rerun sensors-detect?

---

### Post by Michaelg14 on 2008-12-17
I have re-run sensors-detect but not knowing anything else I just chose the default responses.  I did seem to get a lot of "to be written" so I am assuming there are probably no drivers for this cpu.

---

### Post by Michaelg14 on 2008-12-19
Don't know how I missed it but sensors-detect wanted to add 

```
it87
```

to etc/modules.  As soon as I let it do that it worked.  Some of the sensors are mislabeled but that's easy to fix.

---

