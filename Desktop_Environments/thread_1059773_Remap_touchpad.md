---
title: "Remap touchpad"
date: 2009-02-04
forum: Desktop Environments
---

### Post by AndyGibo on 2009-02-04
Hi again

I have a Samsung P28 laptop and need to remap(or disable completely) the right mouse button to act as left mouse button.

I have added this section of code to my xorg.conf file but it hasn't made a difference.

Section "Input Device"
     Identifier "Configured Mouse"
     Driver "mouse"
     Option "Core Pointer"
     Option "Device" "/dev/input/mice"
     Option "Protocol" "Auto"
     Option "ButtonMapping" "1 1 3 4"
EndSection

Can anyone please give me some advice!?

---

