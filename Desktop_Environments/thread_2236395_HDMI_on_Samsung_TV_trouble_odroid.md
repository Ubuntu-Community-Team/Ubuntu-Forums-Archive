---
title: "HDMI on Samsung TV trouble odroid"
date: 2014-07-26
forum: Desktop Environments
---

### Post by z-me-x on 2014-07-26
I have so many trouble with my Samsung TV and my odroid. Both connected via HDMI. If the TV is on and i start my odroid, all is fine i get a display and xserver is working well.

If i switch off the TV, switch it on after a while, i get no HDMI input.

I check this via xrandr -d :0 and get my resolution of my screen and that is connected on HDMI0...
I must restart lightdm and get back my display.

Sometimes i dont get a display via xrandr, then i must reboot the hole odroid.

I tryed out different boot.scr and configure the xorg.conf but no luck.

All this happens after last three kernel updates.

I sit on this problem since weeks and i don't get any solution. I hope somebody is out there, who can help me out.

Thanks!

---

### Post by z-me-x on 2014-07-28
I have the same error with another odroid and complete other TV. Tested now on Panasonic TV as well. I have the same fault. If i unplug HDMI connection and reconnect, the screen wents blank and nothing happens.

---

### Post by mikewhatever on 2014-08-07
I don't have a Samsung or Panasonic TV to test, but can't reproduce the problem with the one there is (an old piece of junk called Benco). In other words, unpluggin and repluggin HDMI brings the picture right back.
You might want to check the Xorg logs in /var/log - <less /var/log/Xorg.0.log>.
Also try asking at the dedicated Odroid forum, they might know better.

---

