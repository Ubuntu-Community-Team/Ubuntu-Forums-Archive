---
title: "Quickly enable/disable TwinView"
date: 2008-07-12
forum: Desktop Environments
---

### Post by mikazo on 2008-07-12
Hi,

I have a TwinView setup running on my Ubuntu 8.04 box with an Nvidia 6200.

I've heard that it's unwise to run intensive 3D applications (games) while running dual monitors from one card. This is how one video card died that belonged to my friend, according to him.

So with that in mind, is there any way to quickly enable and disable TwinView without having to change configuration files and reboot and everything, so I can save wear and tear on my video card?

Thanks.

---

### Post by overdrank on 2008-07-12
> **mikazo said:**
> Hi,

I have a TwinView setup running on my Ubuntu 8.04 box with an Nvidia 6200.

I've heard that it's unwise to run intensive 3D applications (games) while running dual monitors from one card. This is how one video card died that belonged to my friend, according to him.

So with that in mind, is there any way to quickly enable and disable TwinView without having to change configuration files and reboot and everything, so I can save wear and tear on my video card?

Thanks.

HI and you can do this with nvidia settings
```
gksu nvidia-settings
``` just do not save the configuration to the Xorg.

---

### Post by tkoco on 2010-08-12
> **overdrank said:**
> HI and you can do this with nvidia settings
```
gksu nvidia-settings
``` just do not save the configuration to the Xorg.

Thank you. While most applications behave in the twinview environment, the occasional one like DOSBOX need a single monitor. Your suggestion is a viable workaround.

---

