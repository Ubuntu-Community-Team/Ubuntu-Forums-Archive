---
title: "Resolution change issue"
date: 2012-06-21
forum: Desktop Environments
---

### Post by Magellan1186 on 2012-06-21
Hello Community,

       I have a display resolution issue with Xubuntu 12.04. This system is installed on ASUS AT4NM10T-I and used as NAS (storage + torrents) with remote access via RealVNC only, so there is no physical monitor connected. The only display is seen in the system is LVDS1 with resolution 1024x768 according to xrandr. I would like to have 1280x1024 there.
       The steps I made:

~$ cvt 1280 1024
# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

~$ xrandr --newmode "1280x1024_60.00" 109.00 1280 1368 1496 1712 1024 1027 1034 1063 -hsync +vsync

~$ xrandr --addmode LVDS1 "1280x1024_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26

So, it looks like --addmode doesn't work and I don't have a clue why.
Could you please help me to resolve this issue?

Thank you very much in advance.
-- 
My best regards,
Ilya.

---

### Post by Jose Catre-Vandis on 2012-06-21
Need a bit more information about your NAS hardware (graphics capability) and OS setup to offer help on RealVNC. But maybe worth trying the native apps of vino-server and vinagre.


If you have X running on your NAS, why not just ssh -X or ssh -Y in remotely if you need to access a graphical app on your NAS.

Otherwise just ssh and let the cli do the talking

---

### Post by Magellan1186 on 2012-06-21
But I'm not really sure that the issue is RealVNC related. When I create a separate virtual desktop in RealVNC with any resolution it works (the issue however is that I can't have one qBittorrent in all virt. desktops). I'd like to solve resolution issue within :0 desktop, which, I believe, displays my physical desktop, limited without monitor to lower resolution.
When I connect a real monitor I can switch to it from LVDS and there I have 1280x1024.

---

