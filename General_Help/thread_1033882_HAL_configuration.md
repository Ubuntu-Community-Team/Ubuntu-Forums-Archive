---
title: "HAL configuration"
date: 2009-01-07
forum: General Help
---

### Post by Cl0ud9 on 2009-01-07
I am trying to figure out how to disable the pointing stick on my laptop in Ubuntu 8.10, but I haven't had much success. I have stumbled onto a solution via Google that involved editing xorg.conf. The solution is to change
```

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver "mouse"
 Option "CorePointer"
 Option "Device" "/dev/input/mice"
 Option "Protocol" "ExplorerPS/2"
 Option "ZAxisMapping" "4 5"
 Option "Emulate3Buttons" "true"
EndSection

```
to
```

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver "mouse"
 Option "CorePointer"
 Option "Device" "/dev/input/mouse0"
 Option "Protocol" "ExplorerPS/2"
 Option "ZAxisMapping" "4 5"
 Option "Emulate3Buttons" "true"
EndSection

```
with "Option "Device" "/dev/input/mouse0"" being the difference.

In Ubuntu 8.10 it seems this section was automatically commented out and now HAL is used instead of xorg.conf. My question is how can I apply the same changes in HAL as shown in the above xorg.conf section.

---

### Post by whoop on 2009-01-07
Maybe this is a stupid remark (I am no laptop expert), but this hardware feature might be configurable via the BIOS.

---

### Post by Cl0ud9 on 2009-01-07
Thank you for the reply, but BIOS doesn't help me here. I can disable the touchpad and pointing stick all in one in BIOS, but not just the pointing stick.

---

### Post by Ayuthia on 2009-01-07
You might try this link:
[http://bbs.archlinux.org/viewtopic.php?pid=456488#p456488](http://bbs.archlinux.org/viewtopic.php?pid=456488#p456488)
It is for Arch, but the configuration should be same.  The example you should look at is in post #13.  Hope that helps.

---

