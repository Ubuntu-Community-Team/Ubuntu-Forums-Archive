---
title: "Is there emulators for LINUX for CPS1 and CPS2 changer CAPCOM consoles?"
date: 2010-01-07
forum: Gaming &amp; Leisure
---

### Post by frenchn00b on 2010-01-07
Is there emulators for LINUX for CPS1 and CPS2 changer CAPCOM consoles?

Thanks if it exists by chance. 

Kawaks 1.59  is the one for windows xp

---

### Post by farrell2k on 2010-01-07
mame?

---

### Post by frenchn00b on 2010-01-07
> **farrell2k said:**
> mame?

from apt-cache search:
```
xmame-common - Multiple Arcade Machine Emulator
xmame-sdl - SDL binaries for the Multiple Arcade Machine Emulator
xmame-svga - SVGALIB binaries for the Multiple Arcade Machine Emulator
xmame-x - X binaries for the Multiple Arcade Machine Emulator
xmess-common - Support files for the Multi Emulator Super System
xmess-sdl - SDL binaries for the Multi Emulator Super System
xmess-x - X binaries for the Multi Emulator Super System
advancemenu - A front-end to run the Advance*, MAME, MESS, etc. emulators
```

**Are you really sure? which one?**

---

### Post by Grishka on 2010-01-08
> **farrell2k said:**
> mame?

I think not. though MESS seems to have some preliminary CPS systems support, and more thorough support will be added when more games are successfully dumped. looks like at this time [Street Fighter Zero](http://mess.redump.net/sysinfo:sfzch), and [Destiny of an Emperor II](http://mess.redump.net/sysinfo:wofch) can be played.

---

### Post by CharmyBee on 2010-01-08
> **Grishka said:**
> I think not. 
I think so. I've always used MAME to play the CPS games on Linux, and they worked as they should.
I wouldn't ever turn to MESS for a substitute for what can be done well on MAME already (even though, it's the same codebase)

---

### Post by Grishka on 2010-01-08
> **CharmyBee said:**
> I think so. I've always used MAME to play the CPS games on Linux, and they worked as they should.
I wouldn't ever turn to MESS for a substitute for what can be done well on MAME already (even though, it's the same codebase)

then I stand corrected. I find it tough to find a convenient and up-to-date compatibility list for MAME, hence mine ignorance in this matter. :)

---

### Post by frenchn00b on 2010-01-10
> **Grishka said:**
> then I stand corrected. I find it tough to find a convenient and up-to-date compatibility list for MAME, hence mine ignorance in this matter. :)

 it seems to work. thank you
```
xmame.SDL -fullscreen -scale 2 -jt 5 myfolderoffiles/myfile.zip  or  myfolderoffiles/myfile.bin 
```

---

