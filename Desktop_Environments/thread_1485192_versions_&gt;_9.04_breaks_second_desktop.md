---
title: "versions &gt; 9.04 breaks second desktop"
date: 2010-05-16
forum: Desktop Environments
---

### Post by billschu on 2010-05-16
All the Ubuntu versions below are fresh installs, no upgrades.  This issue popped up when I went to move my ultra-reliable 9.04 media player to 10.04.  Subsequent investigation indicates this problem actually began with 9.10, I just never used a 9.10 second monitor in this way before.

In all versions I am cutting and pasting the xorg.conf from the preview in nvidia-settings to get the second monitor to work when using the proprietary drivers because the apply button has never worked for me.

first, my configs..
2 pcs both using same 2 monitors via kvm and hdmi switches
CRT-0 1920x1200 (Dell flat panel driven thru vga)
DFP-0 1920x1080 (Asus flat panel driven thru hdmi)
PC1 - Dual-core E8400 - geForce 9400GT
PC2 - Quad-core E8400 - geForce 9300

PC1 - ubu9.04-i386 - Nvidia 180.44 works
PC1 - ubu10.04-amd64 - Nvidia 195 doesn't work
  PC1 - ubu10.04-amd64 - Nvidia 173 doesn't work
     PC1 - ubu10.04-amd64 - open-driver works
  PC1 - ubu10.04-i386 - Nvidia 195 doesn't work
    PC2 - ubu9.10-i386 - Nvidia 185.18.36 doesn't work
PC2 - ubu9.10-i386 - open-driver works

By "doesn't work" I mean right-click/Create Launcher does not add an icon to the second desktop and icons from the primary desktop cannot be dragged to the second desktop - sometimes you can drag an icon from the menu to the second desktop but then you can't move it from it's original position.  Separately (and not an issue for me but in case anyone decides to tackle this) also broken is the ability to position and add panels on the second monitor.

I realize proprietary drives are not supported, but since Ubuntu is lethargic at best for hi-def video playback without them (among other things) and since 180 works fine on ubu9.04 and both 173 and 195 are broken in 10.04(and, I assume 9.10) I'm hoping it has something to do with the Ubuntu driver installation routines.

TIA

---

