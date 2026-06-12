---
title: "Trackpad support on Toshiba Satellite U940-100"
date: 2021-12-16
forum: Desktop Environments
---

### Post by wheeto86 on 2021-12-16
Hello,

I'm having trouble getting a trackpad to work at all on 20.04.3: the device appears to be recognized, but I'm not getting any input from it. The hardware was working fine in Windows immediately prior to me installing Ubuntu.


```
xinput --list-props "SynPS/2 Synaptics TouchPad" | grep Capabilities
    Synaptics Capabilities (361):    1, 0, 0, 1, 1, 1, 1

```

Steps tried so far:
[LIST]
[*]enable and disable "Legacy support" in BIOS - no change.
[*]Enable and disable trackpad using keyboard combination (fn-F5 on this machine). An icon appears when this is pressed to show either enabled / disable, but no change in behaviour.
[/LIST]

Any suggestions?

Thanks!

---

