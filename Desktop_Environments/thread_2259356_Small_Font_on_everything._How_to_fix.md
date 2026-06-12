---
title: "Small Font on everything. How to fix?"
date: 2015-01-03
forum: Desktop Environments
---

### Post by singhrh on 2015-01-03
Help! New to Ubuntu (and Linux). Mostly happy with it but recently for no reason my fonts have gone very small on the menus, pop dialogs and other places. 


I am running the following: 
Ubuntu 14.04 LTS (64Bit)
processor intel core 2 quad q8200
graphics Geforce 8800 GS/PCIe/SSE2
using Nvidia binary driver - Version 331.113 from nvidia-331 (proprietary, tested)
Monitor is a Dell E176FP (old 17" monitor that I had lying around)


I have tried to modify the xorg.conf file by adding the line:
option "DPI" "96 x 96"
but that did not have any effect. 


Additionally, I have two accounts set up on this machine, ona adminstrator and one Standard user. The administrator account (mine) has the small font issue however the standard user account (my kids) does not seem to have this issue. 

Any and all help is greatly appreciated. 

Thanks

---

### Post by CantankRus on 2015-01-04
Try these 2 terminal commands...
```
gsettings reset com.canonical.Unity.Interface text-scale-factor
gsettings reset com.ubuntu.user-interface scale-factor
```

The change will be instant if this is the cause.

---

### Post by singhrh on 2015-01-04
I cannot thank you enough CantankRus!!!!
I only had to use the first line to fix my small text issue (and it was immediate as you pointed out). Have not tried the second line you suggested.....I don't want to fix something that is no longer broken.

also I presume that the fix is permanent as I have rebooted and the text remains large size. Let's hope it stays this way now.

---

