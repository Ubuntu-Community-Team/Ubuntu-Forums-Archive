---
title: "Vostro 3300 how to disable touchpad? Ubuntu 10.04 32 bit"
date: 2011-02-13
forum: Dell Ubuntu Support (CLOSED)
---

### Post by dpiwowarski on 2011-02-13
Hi.
I have bought dell vostro 3300. Ubuntu 10.04 works great on this machine besides one small thing. Special key to disable touchpad doesn't work. Is there any solution to make this key work?

---

### Post by dpiwowarski on 2012-03-23
A little update one year later.
I'm using 11.10 32bit right now. To disable the touchpad:
```
xinput --set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 0
```
to enable it:
```
xinput --set-prop "SynPS/2 Synaptics TouchPad" "Device Enabled" 1
```

---

