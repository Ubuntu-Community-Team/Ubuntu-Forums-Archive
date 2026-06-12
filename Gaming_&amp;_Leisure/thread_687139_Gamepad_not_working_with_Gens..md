---
title: "Gamepad not working with Gens."
date: 2008-02-04
forum: Gaming &amp; Leisure
---

### Post by hitmanhill on 2008-02-04
Hi.Am running Gens v2.14 mega drive emulator and is it possible to use gamepads with this emulator as I just bought a Powerwave Ps2 controller and cant get it to work.

Is there a more compatible gamepad for this emulator?

Thanks.
Darren.

---

### Post by acoustibop on 2008-02-04
This is a common problem in Gens, Darren.  Try setting your controller configuration four times, and each time use the same directional button/axis for each setting, but a different one each time.  Then after each one, look in your Gens configuration (~/.gens/gens.cfg) and see what it's configured as.  Then edit the configuration with the correct setting for each direction.

Most people find that this is the setting that works:```
P1.Up=4097
P1.Down=4098
P1.Left=4099
P1.Right=4100
```

---

