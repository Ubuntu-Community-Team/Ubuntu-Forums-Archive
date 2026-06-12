---
title: "Still can't manage to enable desktop effects"
date: 2007-08-05
forum: Desktop Effects &amp; Customization
---

### Post by Just-trevor on 2007-08-05
HI
I couldn't enable desktop effects,  so I went to this site, read stuff, then tried to enable the nVidia drivers.
problem, my hardware apparently doesn't need any restricted drivers. So I post a thread and someone tells me to try to install the nvidia drivers from automatixx.  apparently I don't have an nVidia card. doesn't that mean I don't need to install anything or enable anything?  There's probably just something I'm missing.
anyone know what?

---

### Post by Waappu on 2007-08-06
Hi

Type in terminal```
lspci
```to see what video card you have. Post output also here with your xorg.conf

---

### Post by Just-trevor on 2007-08-06
yah, turns out i have an ATI 128 pro ultra...  
02:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
shouldn't that mean I need to install the ATI drivers
there is only nVidia drivers on automatix

---

### Post by Waappu on 2007-08-06
Hi

Sorry but your card can't handle Beryl or Compiz. You can't enable desktop-effect with your card

---

### Post by Chudilo on 2007-08-06
You should still get ENVY and install the latest ATI drivers.
It should make ubuntu run smoother.

---

### Post by Waappu on 2007-08-06
> **Chudilo said:**
> You should still get ENVY and install the latest ATI drivers.
It should make ubuntu run smoother.

Hi

I think not. Rage is so old card and open source "ati" driver is best one for it

---

### Post by Just-trevor on 2007-08-06
Ok, thanks waappu

nice to know its my card, not me

---

