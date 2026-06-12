---
title: "KDE4.2 dead slow on Intel chipset"
date: 2009-03-15
forum: Desktop Environments
---

### Post by FinnCoder on 2009-03-15
Hi

I installed KDE4.2 on my Intrepid laptop (Acer Extensa 5220) and it performs mostly ok, but 3D OpenGL apps are really slow (and PulseAudio doesn't work). I mean something like 10 fps versus 40 fps on Gnome for a full-screen application. Effects are switched off. My laptop has Intel's graphic chipset. Any idea what causes this? And again: no problems with Gnome + Compiz on the same computer.

I really like the look & feel of KDE4.2 and hope that it will be the default Ubuntu desktop in the future :)

---

### Post by roach of discord on 2009-04-20
Unfortunately, I have the same issue. It is just SO slow on my intel integrated graphics, while Gnome is not. Right now I've surrendered and am running Gnome..but not with happiness..I really don't like Gnome. I think it has something to do with Plasma and the Intel driver. If you kill plasma, things get fast..but then, you have no desktop..soo...not much help. My older PC had an nvidia card, and kde4 worked excellent on it..so it's definitely the driver. I think sometime soon I'm just going to buy a cheap nvidia card. It's just too much trouble.

---

### Post by apparle on 2009-04-20
I had heard that KDE4 runs better on intel cards rather than nvidia/ATi
Anyways how did you check the fps. I wanna check mine

---

### Post by roach of discord on 2009-04-20
For me that's the opposite. From my experience NVIDIA supports kde4 quite well. I have a fairly basic geforce card, and kde4 was lightning fast. This intel though..it's so sluggish and unbearable.

---

### Post by inobe on 2009-04-20
i wouldn't run kde on that chipset, xubuntu would be more forgiving.

---

### Post by roach of discord on 2009-04-21
I got bored and started playing around with my Xorg.conf.

Try adding Option     "AccelMethod"                  "XAA"

in your xorg.conf file. It seems to have helped the speed thing in kde4, atleast, from what I can tell so far.

---

