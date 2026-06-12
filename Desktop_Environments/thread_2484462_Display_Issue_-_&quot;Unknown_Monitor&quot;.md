---
title: "Display Issue - &quot;Unknown Monitor&quot;"
date: 2023-02-27
forum: Desktop Environments
---

### Post by Peter_Smerdon on 2023-02-27
I cannot change display settings from the default 4:3 despite using a 16:9 display.

Display settings show "Unknown Display"

The only available option (default) is "1024x768 (4:3)" which results in a horizontally stretched 4:3 display on 16:9 monitors.

I've tried multiple monitors - Samsung and Viewsonic - 4 models using both VGA and HDMI connections
I am using an NVidia GeForce710 graphics card - NVidia drivers are installed.

I get the same results using the motherboard's integrated graphics.

I ran "xrandr" and "xrandr --listmonitors" - they both report "failed to get size of gamma for output default"

I cannot find a listmonitors.xml file at /home/.config/ (using terminal command ls -la)

Ubuntu is Ver 22.04.1 LTS 64bit on an Intel i5-3330.

Is the missing listmonitors.xml causing this grief?

All help appreciated.

Thanks in advance.

Peter Smerdon

---

