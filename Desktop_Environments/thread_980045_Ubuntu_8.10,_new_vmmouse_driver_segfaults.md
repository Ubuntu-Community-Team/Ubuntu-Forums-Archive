---
title: "Ubuntu 8.10, new vmmouse driver segfaults"
date: 2008-11-12
forum: Desktop Environments
---

### Post by ejsing on 2008-11-12
After updating to the newest version of the vmmouse driver (which recently had problems with Ubuntu 8.10) I now get a segfault upon starting my X-server.

Attached screenshot shows the output in the X-server log file.

---

### Post by er4z0r on 2008-12-05
> **ejsing said:**
> After updating to the newest version of the vmmouse driver (which recently had problems with Ubuntu 8.10) I now get a segfault upon starting my X-server.

Hi I had a similar problem and got it fixed by reducing the amount of parameters I passed to the module in my xorg.conf:

```

Section "InputDevice"
        Identifier      "VMware Mouse"
        Driver          "vmmouse"
        Option          "CorePointer"
#       Option          "Device"                "/dev/input/mice"
#       Option          "Protocol"              "ps/2"
#       Option          "ZAxisMapping"          "4 5"
#       Option          "Emulate3Buttons"       "true"
EndSection

```

Some Specs:
Host is Macbook Pro, running OS 10.5.5 an VMWare Fusion 2.0.1 (128865)
Note: VMwaretools created the xorg.conf with the above params but with mouse instead of vmmouse. I guess this was done as a workaround for an [older vmmouse-bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-vmmouse/+bug/248521").

Anyway, hope this helps.

---

