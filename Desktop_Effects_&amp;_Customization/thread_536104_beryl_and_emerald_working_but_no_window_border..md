---
title: "beryl and emerald working but no window border."
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by linux4m3 on 2007-08-27
I have beryl working properly and i have no window border so then i installed emerald and put a theme and click on it. But still i have no window border why. I need help with.

---

### Post by Fire(storm) on 2007-08-27
[https://answers.launchpad.net/ubuntu/+question/5317](https://answers.launchpad.net/ubuntu/+question/5317)

I had the same problem. I followed several different guides, and this fixed it.

---

### Post by BottomsUp on 2007-08-27
do you know if this will work for ATI cards? I'm having the same problem and have an ATI x1900

---

### Post by linux4m3 on 2007-08-27
Fire(stone) thanks!! It worked great. :)

---

### Post by justcycling on 2007-08-28
I tried it but I am still having the same issue where the border doesnot change to what the theme should be.  Here is the Device section from my xorg.conf:

Section "Device"
        Identifier      "ATI Technologies Inc Radeon Mobility M7 LW [Radeon  Mobility 7500]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
        Option "AddARGBVisuals" "True"
        Option "AddARGBGLXVisuals" "True"
        Option "NoLogo" "True"
EndSection

Any ideas?  I am trying to use the LiNsta3 theme.

Thanks.

---

### Post by linux4m3 on 2007-08-28
Try a different theme to see if that works. Or make that you wrote the right things in your xorg.conf file. I really don't anymore than you. I just tried exacltly what you did and it worked for me.

---

