---
title: "Persistent image with nvidia quadro nvs 295"
date: 2011-04-25
forum: Desktop Environments
---

### Post by MgFrobozz on 2011-04-25
I'm going nuts with a video driver problem on a new pc, on which I've installed ubuntu 10.10.

This is an nVidia (details below). I spent a couple of days puzzling about why the system would start to boot, then the screen would go black with no error messages. Then a friend told me that ub 10.10 didn't handle newer nvidia cards correctly, and I'd need to get the driver from the nvidia website.

I installed the proprietary driver, and everything works nearly perfectly except ... every once in a while, part of an image from a web page will become persistent in the driver memory. Even after killing the browser (and ensuring it's not in the "ps" list), the image will reappear if the foreground window has white areas that overlap where it was in the driver. This also happens if all windows are minimized, and the wallpaper has white areas. Any non-white regions (in windows or wallpaper) will hide the persistent image.

This happens once every 2-3 days, and the only way I can find to eliminate it is to reboot. I'd greatly appreciate any suggestions for a fix, or even a less time-consuming work-around.

```

> lspci | grep nVidia
01:00.0 VGA compatible controller: nVidia Corporation G98 [Quadro NVS 295] (rev a1)

> uname -srvmpio
Linux 2.6.35-28-generic #50-Ubuntu SMP Fri Mar 18 18:42:20 UTC 2011 x86_64 unknown unknown GNU/Linux

> cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.10
DISTRIB_CODENAME=maverick

```

---

### Post by securitymeddler on 2012-06-22
Ever find a solution to this? I am having video issues also with the 

VGA compatible controller: NVIDIA Corporation G98 [Quadro NVS 295] (rev a1)

---

