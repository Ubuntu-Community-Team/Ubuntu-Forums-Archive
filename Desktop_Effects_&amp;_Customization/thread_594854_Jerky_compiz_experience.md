---
title: "Jerky compiz experience"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by tony_gustafsson on 2007-10-28
With the new** 8.42.3 ATI drivers** i can finally enable compiz fusion. But while the 3D graphics run kind of smooth, the whole experience was jerky. Simple things like scrolling a webpage takes really long time. Firefox is worst. So I have to disable compiz again, but i would really love to make it work.

I don't know, but it SEEMS like the graphic card can handle it, but stops for a second once in a while. I tried setting the colors to 16-bit in xorg.conf but i couldn't start X after that. Switched back. Someone said that would work. I do NOT have xserver-glx installed.

My system:
AMD64 3200+
2 GB RAM
ATI Radeon X1600Pro
Ubuntu 7.10 Gutsy 32-bit desktop edition

Xorg.conf:
[ATTACH]48136[/ATTACH]

fglrxinfo:
[ATTACH]48131[/ATTACH]

glxgears:
[ATTACH]48132[/ATTACH]

compiz
[ATTACH]48130[/ATTACH]

glxinfo
[ATTACH]48133[/ATTACH]

Thank you
/Tony

---

### Post by Forlong on 2007-10-28
> **tony_gustafsson said:**
> With the new** 8.42.3 ATI drivers** i can finally enable compiz fusion. But while the 3D graphics run kind of smooth, the whole experience was jerky. Simple things like scrolling a webpage takes really long time. Firefox is worst.
Same here. I just went back to the open radeon driver. If you don't want (or can't) do that, stick to fglrx from the repos + Xgl for now.

Future versions will hopefully work better with AIGLX/Compiz

---

### Post by carlosjuero on 2007-10-28
(New to Gutsy here)

I had the same sorty of jerky performance with Compiz on a fresh Ubuntu install (which is why I don't run it now [Compiz that is]) - the first time it was because the ATI drivers didn't take, I fixed that problem but it really isn't worth the graphics slowdown for some glitter. I hope that future ATI releases will be more in line and fluid with this, as I like the variety and looks of Compiz - just not at a compromise to performance.

---

### Post by tony_gustafsson on 2007-10-28
> **Forlong said:**
> Same here. I just went back to the open radeon driver. If you don't want (or can't) do that, stick to fglrx from the repos + Xgl for now.

Future versions will hopefully work better with AIGLX/Compiz

Does old fglrx + xgl work with compiz? No? Doesn't compiz need AIXGL?

---

### Post by Forlong on 2007-10-28
> **tony_gustafsson said:**
> Does old fglrx + xgl work with compiz?
Yes, of course.
> **tony_gustafsson said:**
> Doesn't compiz need AIXGL?
No. you can either use Xgl, AIGLX or Nvidia.

---

### Post by GIFRATE on 2007-10-31
I have the same situation here.
Installed new ATI drivers to use compiz. It works but it's jerky, as mentioned above. 

My hardware is:
Inspiron 1521
AMD Turion X2 56
1 Gb RAM
ATI RADEON Xpress 1270

---

### Post by Forlong on 2007-10-31
Like I said, just stick to fglrx from the repos + Xgl (sudo apt-get install xserver-xgl) for now.

---

### Post by tony_gustafsson on 2007-11-09
I don't have to make a XGL session or anything like that? I know i had to in ubuntu6. Just install xgl-server, and the old ati drivers, and it will work?

---

### Post by Forlong on 2007-11-09
> **tony_gustafsson said:**
> I don't have to make a XGL session or anything like that? [...]. Just install xgl-server, and the old ati drivers, and it will work?
That's right. :)

---

### Post by tony_gustafsson on 2007-11-12
> **Forlong said:**
> That's right. :)

I just tried it.. I activated the default ati prop drivers, and installed xserver-glx... in that mode it actually were better with compiz on than off. With compiz on i had the same problem as before. With compiz of things like moving a window took forever :)

Couln't it be a setting in bios or something?

---

