---
title: "pSX emulator crashes on start"
date: 2012-02-19
forum: Emulators
---

### Post by BrezelGoring on 2012-02-19
I am having a tedious issue with this, after I put the BIOS, as i am asked to, the emulator starts, i see the black frame (i'm using ubuntu 10.04, with GNOME classic) with nothing inside and then it crashes for no apparent reason, i don't get to see the yellow playstation sign neither. it's like the 1° frame the window is there, the next one it dissapears.
How do I solve this?
**TL;DR** - I run it, put the BIOS, and it crashes as soon as you click OK.
System specs:
1GB RAM
1.67 GhZ AMD Sempron Processor (SingleCore)
Don't really know the video card, it's capable of running no$gba (NDS) at 90% efficiency and warzone 2100 at 20 FPS, GBA and NES games are at full efficiency.
Ubuntu 10.04 with GNOME classic.
Thanks.

**EDIT: **Forgot to add with emulator I am using.[]("http://psxemulator.gazaxian.com/pSX_linux_1_13.tar.bz2") [HERE]("http://psxemulator.gazaxian.com/pSX_linux_1_13.tar.bz2")

---

### Post by robhamm on 2012-03-19
> **BrezelGoring said:**
> I am having a tedious issue with this, after I put the BIOS, as i am asked to, the emulator starts, i see the black frame (i'm using ubuntu 10.04, with GNOME classic) with nothing inside and then it crashes for no apparent reason, i don't get to see the yellow playstation sign neither. it's like the 1° frame the window is there, the next one it dissapears.
How do I solve this?
**TL;DR** - I run it, put the BIOS, and it crashes as soon as you click OK.
System specs:
1GB RAM
1.67 GhZ AMD Sempron Processor (SingleCore)
Don't really know the video card, it's capable of running no$gba (NDS) at 90% efficiency and warzone 2100 at 20 FPS, GBA and NES games are at full efficiency.
Ubuntu 10.04 with GNOME classic.
Thanks.

**EDIT: **Forgot to add with emulator I am using. [HERE]("http://psxemulator.gazaxian.com/pSX_linux_1_13.tar.bz2")

I had issues with it, as well. Did you do a search for dependencies? It's got a few, and the deb doesn't isntall them or warn you about them. The list of dependencies isn't quite specific enough, if I recall, and I ended up searching synaptic for things related to the things on the list. It is, however, my favorite PSX emulator.

---

### Post by dfreer on 2012-03-20
Run the emulator from the commandline, and post any output. Also, run the ldd command against the binary:
```
ldd ./pSX
```

---

