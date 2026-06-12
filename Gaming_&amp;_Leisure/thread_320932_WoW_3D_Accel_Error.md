---
title: "WoW 3D Accel Error"
date: 2006-12-18
forum: Gaming &amp; Leisure
---

### Post by Aifel on 2006-12-18
So, I'm trying to get WoW working under OpenGL. I can run it under D3D (the default), but when trying to run it under OpenGL, a window will come up stating "Unable to start 3D acceleration". 

After running glxinfo, I get this.
 glxinfo | grep rendering
libGL warning: 3D driver claims to not support visual 0x42
direct rendering: Yes

Can someone help?
Also, my video card is a ProSavage8 KM266/KL266, according to an lspci. I've also been having trouble installing the latest DRI drivers, the reason for it is because I don't have the latest kernel modules installed, even though I'm pretty sure I do. I'm running Edgy on 2.6.17-10-generic.

---

### Post by hikaricore on 2006-12-18
Are you running in 24bit or 16bit colour?  I get that error on my system when trying to start opengl mode in 16bit colour.. Just an idea lol.

---

### Post by Sammi on 2006-12-18
If you don't have much experience, then I can tell you that the colour depth is configured in this configuration file: /etc/X11/xorg.conf

As it's a system file, you need to the root to edit it. You can edit it in root by doing this command:
```
gksudo gedit /etc/X11/xorg.conf
```
Find a line, that looks like this:
```
    DefaultDepth    24
```If it says anything else than 24(like probaly 16) then change it to 24.

---

### Post by Aifel on 2006-12-18
OK, I changed my XOrg conf, but it still doesn't work (before restarting). I will try after I restart my computer, which is right about now.

---

### Post by Aifel on 2006-12-18
OK, it works, but it's super slow, and when I try to change my options, the game crashes. Anyway, thanks for the help...

---

### Post by Sammi on 2006-12-18
Yeah I believe the game crashes for everyone right now when you change video setting while in opengl mode. Try running the game in d3d mode, change the settings you want to, close, and run in opengl again.

About the slow performance, you said you are using a ProSavage8 KM266/KL266 grafics card. I just tried to look it up, and I hate to burst your bubble and I want you to know that I know little about this card, other than that it's motherboard intergrated... Well the thing is that integrated cards are usually not very good at games. You should think about getting a Nvidia instead if it's possible :neutral:

But it may also be that there is something wrong, which can be fixed. Please try checking out if there are newer drivers for your grafics card, and if there are possible tweaks, which could make it perform better. Do a forum search first, then google.

Oh and anyway, what are your other system specs? Cpu, RAM...

---

### Post by Aifel on 2006-12-19
Here's my CPU specs...

```

cat /proc/cpuinfo 

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Celeron(R) CPU 2.40GHz
stepping        : 9
cpu MHz         : 2404.551
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe up cid xtpr
bogomips        : 4816.24



```

---

### Post by HolyLiaison on 2006-12-19
Upgrading your video card would definitely be tops on your priority list. It would help out greatly.   :)

And if you don't have at least 1GB of RAM I'd also upgrade some there too.

Glade you got it working though. Hope everything works out.

---

### Post by Sammi on 2006-12-19
To compare I have:
* Intel Centrino 1,7 GHz CPU(to compare a Centrino processor with other processors one should add about 1 GHz, making it the equivalent of a 2,7 GHz regular CPU)
* 1 GB RAM
* Nvidia 6800 go grafics card with 256 MB RAM

I get between 20 and 30 fps, with all video settings set on high.

---

