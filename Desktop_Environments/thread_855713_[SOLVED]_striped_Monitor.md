---
title: "[SOLVED] striped Monitor"
date: 2008-07-10
forum: Desktop Environments
---

### Post by bucksquare on 2008-07-10
neebie with ubuntu serverw/gui just installed. Ubuntu 8.04 monitor works fine. monitor has stripes.
 Please help. Thanks

---

### Post by overdrank on 2008-07-10
> **bucksquare said:**
> neebie with ubuntu serverw/gui just installed. Ubuntu 8.04 monitor works fine. monitor has stripes.
 Please help. Thanks

HI and welcome, > **bucksquare said:**
> Ubuntu 8.04 monitor works fine. monitor has stripes.
Ok does the monitor work fine or does the monitor have stripes? what is the model of the graphics card?

---

### Post by bucksquare on 2008-07-10
monitor works fine using ubuntu desktop.
The desktop gui in server has two problems:1) the display has stripes, line of white transversing the background 2) the screen is split, applicatios is in the middle of the screen and to get to the network icon the mouse has to go all the way to right and then appears on the left.

Thanks

---

### Post by bucksquare on 2008-07-12
hello,
 i think the monitor has stripes.

thanks.

---

### Post by overdrank on 2008-07-12
> **bucksquare said:**
> hello,
 i think the monitor has stripes.

thanks.

HI and as I asked before what is the model of the graphics card? Have you tried to boot into recovery mode and use the xfix option?

---

### Post by bucksquare on 2008-07-12
no I have not tried that. I need again the path to identify my installed hardware.

Thanks

---

### Post by overdrank on 2008-07-12
> **bucksquare said:**
> no I have not tried that. I need again the path to identify my installed hardware.

Thanks

HI and I see in your other post that the graphics is a vga chrome 9hc Igp. Which are not well supported in linux, I am assuming that is integrated on the motherboard and will share the systems memory. How much memory is installed on the system? If the xfix option does not work in recovery mode then you can try and use the ctrl, alt, F1 keys and this will bring you to the command prompt and you can use this command to configure your xorg ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

