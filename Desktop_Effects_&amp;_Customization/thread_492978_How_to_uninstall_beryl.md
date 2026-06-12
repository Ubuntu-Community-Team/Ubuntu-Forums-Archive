---
title: "How to uninstall beryl?"
date: 2007-07-05
forum: Desktop Effects &amp; Customization
---

### Post by lukanikos on 2007-07-05
Can somebody please tell me how to uninstall beryl completely from obuntu?

---

### Post by reckless2k2 on 2007-07-05
open synaptic, search beryl.....then check completely remove. reboot. that should do the trick.

from command line....

sudo apt-get remove beryl

---

### Post by lukanikos on 2007-07-07
How can I remove the rest?

```
lukanikos@lukanikos:~$ sudo apt-get remove beryl
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package beryl is not installed, so not removed
The following packages were automatically installed and are no longer required:
  beryl-core beryl-settings-bindings libberylsettings0 beryl-settings
  beryl-plugins libemeraldengine0 beryl-plugins-data libberyldecoration0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
lukanikos@lukanikos:~$ 
```

---

### Post by bigken on 2007-07-07
sudo apt-get autoremove

---

### Post by lukanikos on 2007-07-07
Cool!!!!
Thanks!!!

All removed exept beryl manager it's still there

How can I remove this one?

---

### Post by bigken on 2007-07-07
add remove programs or try sudo aptitude remove beryl

---

### Post by lukanikos on 2007-07-08
How do I remove emerald theme manager?

---

