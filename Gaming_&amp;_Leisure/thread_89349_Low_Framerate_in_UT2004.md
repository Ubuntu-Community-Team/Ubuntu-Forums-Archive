---
title: "Low Framerate in UT2004"
date: 2005-11-12
forum: Gaming &amp; Leisure
---

### Post by cataath on 2005-11-12
Hi all,

I just installed UT2004ECE on Breezy, and am getting really terrible framerates, especially compared to the same settings on Windows XP. 

I have a AMD Athlon XP 2000+, GeForce 4 TI-4400, 768mb DDR, & am using the official nVidia drivers.

In glxGears (yes, I acknowlegde this is not a benchmark-but it is!) I'm getting a smooth 4220 fps, and in Armegetron at 1024x768 I get a smooth 50+ fps, but in UT2k4 at 800x600 with all settings on low my framerate drops to around 10-15 with just a few bots on an onslaught game.

I Win, I typically get around 40fps with the same game at 1024x768 and the same settings at medium. I was honestly expecting to see better numbers than in Windows, since I usually run games with antivirus/firewalls/services/etc. turned on.

Is there some settings somewhere I'm missing, or at lease is there an nVidia/Catalyst tweaking guide or tool somewhere?

---

### Post by homerhomer on 2005-11-12
are you running the latest version of ut2004? Mine says 3355

---

### Post by cataath on 2005-11-12
Yes. I installed the 3355 patch. I also found the [nVidia guide]("ftp://download.nvidia.com/XFree86/Linux-x86/1.0-7676/README.txt") and, following its instructions, removed the following from xorg.conf:
    Load "dri"
    Load "GLCore"

and added the following under "Device":
    Option "NvAGP" "2"

Rebooted and I still have about the same performance. Bummer. :(

---

### Post by nemnivus on 2005-11-12
Unfortunately the GL renderer in Unreal is subpar compared to the DirectX one in windows.  Usually it's about a 30 percent performance hit, so with that lower end hardware it'll come through in poor frame rates.  You might try recompiling SDL and OpenAL for AthlonXP and relinking them, it definitely helps.  There are some instructions floating around on google.

---

### Post by 3dmaker on 2005-11-12
I had to install my Nvidia drivers to make mine work. Then in the /etc/X11/xorg.conf set the driver thing from "nv" to "nvidia"

---

