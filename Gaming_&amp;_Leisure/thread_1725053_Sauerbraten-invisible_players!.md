---
title: "Sauerbraten-invisible players!"
date: 2011-04-09
forum: Gaming &amp; Leisure
---

### Post by nikefalcon on 2011-04-09
I recently installed sauerbraten on maverick and surprised to see weapons floating in thr air,shooting. Some players and bots seem to invisible.(It worked fine on Lucid) Playing with the graphics settings had no effect. Looking forward to suggestions and solutions.
Thank you

---

### Post by Philsoki on 2011-04-09
> **nikefalcon said:**
> I recently installed sauerbraten on maverick and surprised to see weapons floating in thr air,shooting. Some players and bots seem to invisible.(It worked fine on Lucid) Playing with the graphics settings had no effect. Looking forward to suggestions and solutions.
Thank you
What's the output for:
```
lspci |more
```

Have you installed your video drivers? If yes, have you set them to high performance (Instead of High Quality) if the option is available? I'm thinking Nvidia X Server Open GL settings here...

---

### Post by nikefalcon on 2011-04-09
> **Philsoki said:**
> What's the output for:
```
lspci |more
```Have you installed your video drivers? 
I have never had to install any additional drivers for my intel card....and i don't know how to install them either.

> **Philsoki said:**
>  If yes,  have you set them to high performance (Instead of High Quality) if the  option is available?
How do you set that?

outpt of lspci:
```

lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

```

```

lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:01.0 Modem: Motorola SM56 Data Fax Modem (rev 04)

```

---

### Post by Philsoki on 2011-04-10
Well, if you had it running fine on 10.04 there should be a way to get it running fine on 10.10, even with integrated graphics...

What do you get from:
```
glxgears
```Also, you said you fiddled with the graphics settings... Can you (For the sake of testing) see how Sauerbraten runs with video settings at low and in windowed mode at 800x600 resolution? And if you tried that, well...

Edit: This might come in handy: [http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/intel-graphics-performance-guide-for-ubuntu-904-jaunty-users.html)

---

### Post by nikefalcon on 2011-04-10
glxgears works fine:
```

glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.
424 frames in 5.0 seconds = 84.727 FPS
425 frames in 5.0 seconds = 84.906 FPS
425 frames in 5.0 seconds = 84.906 FPS
^C

```> **Philsoki said:**
> 
Can you (For the sake of testing) see how Sauerbraten runs with video settings at low and in windowed mode at 800x600 resolution? And if you tried that, well...

invisible players still persist in low graphics, windowed, low res mode. :(
Thanks for your help
Going to check out that link now....


Edit: I don't think its a driver related issue, since some player models *are* visible.

---

### Post by Philsoki on 2011-04-10
Did you install it from the repo's or download it from the website?

---

### Post by nikefalcon on 2011-04-10
Got it straight from the repos.
```

aptitude versions sauerbraten
i   0.0.20100728.dfsg-2                           maverick                  500 

```

---

### Post by nikefalcon on 2011-04-11
I don't know what was wrong, but looks like like something was wrong in one of the config files in .sauerbraten. It works properly now, after i deleted the .sauerbraten directory from my home. :)

---

