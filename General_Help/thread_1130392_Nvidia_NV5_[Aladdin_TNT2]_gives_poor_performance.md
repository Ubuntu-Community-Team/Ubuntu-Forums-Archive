---
title: "Nvidia NV5 [Aladdin TNT2] gives poor performance"
date: 2009-04-19
forum: General Help
---

### Post by knight666 on 2009-04-19
Hi.

I'm configuring a server (Ubuntu 8.10) and I was asked to install a GUI for it. It's a very old computer that would have otherwise been thrown away, but I installed GNOME on it anyway. This gave an absolutely abysmal performance, so I dumped it in favor of Xfce.

The way it's set up is that it boots to console, and you type "startx" to get to the GUI. Even after all my tweaking it takes roughly 5 minutes from typing startx to actually launching a program.

The problem is (I think) that I can't run the nvidia driver and have to use the nv driver. Whenever I use the nvidia driver X returns "no screens found". :\

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV5 [Aladdin TNT2] (rev 20)
```

How can I enable the nvidia drivers for this ancient video card?

Thanks in advance.

---

### Post by cinematography on 2009-04-19
> **knight666 said:**
> Hi.

I'm configuring a server (Ubuntu 8.10) and I was asked to install a GUI for it. It's a very old computer that would have otherwise been thrown away, but I installed GNOME on it anyway. This gave an absolutely abysmal performance, so I dumped it in favor of Xfce.

The way it's set up is that it boots to console, and you type "startx" to get to the GUI. Even after all my tweaking it takes roughly 5 minutes from typing startx to actually launching a program.

The problem is (I think) that I can't run the nvidia driver and have to use the nv driver. Whenever I use the nvidia driver X returns "no screens found". :\

```
$ lspci | grep VGA
01:00.0 VGA compatible controller: nVidia Corporation NV5 [Aladdin TNT2] (rev 20)
```

How can I enable the nvidia drivers for this ancient video card?

Thanks in advance.
I'm not sure. It might be better if you just got a new nVidia video card for the cheap from newegg.

---

### Post by txcrackers on 2009-04-20
The legacy drivers might work, but you're still not going to have very snappy graphics with anything "heavy" (which includes both Gnome and KDE). XFCE might be pretty functional, but if you want a snappier UI, go with Fluxbox. It's quite "primitive" compared to the others, but that means it's stripped down and faster.

---

### Post by dcstar on 2009-04-20
> **knight666 said:**
> Hi.

I'm configuring a server (Ubuntu 8.10) and I was asked to install a GUI for it.
........
How can I enable the nvidia drivers for this ancient video card?

Thanks in advance.

You can't, 8.04 will support these old Nvidia cards but 8.10 onwards doesn't.

8.04 server will be supported until 2013, use that.

---

