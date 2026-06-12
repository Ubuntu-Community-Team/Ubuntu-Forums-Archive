---
title: "Disabling one of multiple keyboards"
date: 2009-05-12
forum: General Help
---

### Post by Random Juju on 2009-05-12
I have multiple "keyboards" attached to my system.  One's a real keyboard and the other is a barcode scanner.  Although the barcode scanner acts like a keyboard, I handle events it generates using gizmod and I'd prefer that its input never made it to the normal flow of things in X.

What I'd like to do is have the barcode reader continue to generate events (i.e. through /dev/input/eventN), but have X ignore input from that device.  I'm not quite sure where to start in the whole input stack (hal?).  Can somebody point me in the right direction?

Thanks!

---

### Post by Random Juju on 2009-05-12
Following a suggestion from the [X configuration wiki page](https://wiki.ubuntu.com/X/Config/Input), I discovered that this works (at least for my barcode reader):

```
$ xinput set-int-prop "?Symbol Technologies, Inc, 2002 Symbol Bar Code Scanner" "Device Enabled" 8 0
```

Cheers!

---

