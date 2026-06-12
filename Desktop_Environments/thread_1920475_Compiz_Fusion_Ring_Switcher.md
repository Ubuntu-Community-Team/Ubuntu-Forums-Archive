---
title: "Compiz Fusion Ring Switcher"
date: 2012-02-04
forum: Desktop Environments
---

### Post by Whoop365 on 2012-02-04
I really like the ring switcher plugin, except for the "wobble" affect after choosing a window. It gives me a headache.

Is there a way of editing some of these plugins in terminal? because the "timestep" settings is what is causing it, but you cannot turn in off (to the best of my knowledge)

---

### Post by stinkeye on 2012-02-04
Install compizconfig-settings-manager
```
sudo apt-get install compizconfig-settings-manager
```

Hit alt+F2 and enter ccsm
and change the timestep in the ring switcher plugin to 0.1
Be careful using ccsm as changing some settings will cause compiz not to reload properly.
It is recoverable though and there are plenty of threads to show you how to recover.

---

