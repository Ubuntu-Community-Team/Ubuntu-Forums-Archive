---
title: "1280x1024 Resolution No Longer Shows Up in Monitor Preferences"
date: 2011-03-09
forum: Desktop Environments
---

### Post by slurpee2k5 on 2011-03-09
Hello Everyone,

For some time now, I have been using my laptop as well as an external monitor. The Laptop's native resolution is 1366x768 and the external monitor's resolution is 1280x1024. Up until today, it worked perfectly. I was able to set the resolution of the screens through the Monitor Preferences application to their correct values. However, today when I turned on my computer, the option for 1280x1024 just flat out wasn't there. I restarted my computer and everything but no luck, the option is just gone. I have no idea what could have caused this to happen. I remember yesterday I connected my laptop to another display with a higher resolution for a couple of hours (I was working at another desk) but this definitely should not have deleted 1280x1024 being an option. I tried manually readding 1280x1024 by using xrandr:

$xrandr --newmode fix 109.00 1280 1368 1496 1712  1024 1027 1034 1063 -Hsync +Vysnc

$ sudo xrandr --addmode LVDS fix

But the second command gave this error:

X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26

Can anyone tell me what is wrong?

Thanks.

---

