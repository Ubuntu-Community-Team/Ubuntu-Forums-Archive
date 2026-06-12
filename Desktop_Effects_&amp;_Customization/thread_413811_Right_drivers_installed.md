---
title: "Right drivers installed?"
date: 2007-04-19
forum: Desktop Effects &amp; Customization
---

### Post by SebbeJohan on 2007-04-19
Hi

I'd like to install Beryl but something is bugging me, I don't know whether I have the right drivers installed or not.
As mentionned in the howto, I did:

```
glxinfo | grep direct
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: Yes
```

the yes is a good sign but what about the libGL warning? Is something missing?

my graphic card is ```
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
```

Should I install fglrx instead?
:confused:

---

### Post by SebbeJohan on 2007-04-21
anyway, upgrading to feisty broke my system so I made a fresh new install, and gave it a try. I followed this howto [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

everything works perfectly, \\:D/ so I guess I had to change the driver.

---

