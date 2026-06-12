---
title: "If this is somewhere else - I can't find it"
date: 2010-01-04
forum: Desktop Environments
---

### Post by D-Dan on 2010-01-04
I bought a new 1080p TV last week - max resolution 1920 x 1200. My desktop monitor supports 1650 x 1080. I'd like a dual desktop with the TV - at max native resolution on each, but can't for the life of me get it to work.

please point me in the right direction.

Using:

CCC 9.12
HD4670 (DVI to the desktop monitor, DVI - HDMI on the TV)
Ubuntu 9.10

Cloning works OK, and I can get what I want on Win 7. Just can't figure it out on Ubuntu.

Any help is appreciated - or like I said, if someone has already done this - a link will do :)

TIA

Steve

---

### Post by egravede on 2010-01-05
have you tried editing the xorg.conf with the settings you want?

---

### Post by falconindy on 2010-01-05
Your **1080**p TV will not support a resolution taller than 1080 pixels. That's the definition of what a 1080p screen is. It might support 1920x1080.

---

### Post by D-Dan on 2010-01-06
It does, in actual fact, support 1920 x 1200 (which I can confirm from Windows), but whether it's 1200 or 1080 is not the issue, but rather can I have dual display with different resolutions?

Steve

---

### Post by falconindy on 2010-01-06
> **D-Dan said:**
> ...can I have dual display with different resolutions?
Yep, but you'll need to do the configuration manually via xorg.conf. Some people find XINERAMA works, some don't. Some find xrandr works, some don't. As your video card is an ATI, I'd say start with xrandr.

---

### Post by captain_171 on 2010-01-06
What Video Card you using?
Nvidia or ATI or a intel card?

---

### Post by falconindy on 2010-01-06
> **captain_171 said:**
> What Video Card you using?
Nvidia or ATI or a intel card?

> **D-Dan said:**
> ...

Using:

CCC 9.12
**HD4670** (DVI to the desktop monitor, DVI - HDMI on the TV)
Ubuntu 9.10

...

Unless I'm mistaken, that's a [Radeon 4600 series](http://ati.amd.com/products/Radeonhd4600/index.html).

---

