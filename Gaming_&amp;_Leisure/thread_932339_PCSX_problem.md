---
title: "PCSX problem"
date: 2008-09-28
forum: Gaming &amp; Leisure
---

### Post by xeriouxi on 2008-09-28
Hi!

I seem to have an issue with configuring PCSX. When I go into the options to configure the graphics and press the configure button nothing happens. I'm trying to use Pete's MesaGL Driver but this happens on his XGL2 driver, too. Does anyone know how I can get the configuration working other than having to manually try and configure?

I'm also curious how my version of PCSX is 1.7 RC1? I checked the main site and it hasn't been updated for absolutely ages... has the development page moved elsewhere? I preferably want to stick with PCSX because I can't stand the look and feel of ePSXe with it's GTK1 interface. It also doesn't seem to have the latest version available on Linux unlike the Windows version... maybe they being nice and using GTK2 for the new Linux version? I wish! =P

Thanks for any help! =)

---

### Post by hessiess on 2008-09-28
[http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)

run from download directory. dos not use plugins, so is verry easy to configure.

---

### Post by xeriouxi on 2008-09-28
> **hessiess said:**
> [http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)

run from download directory. dos not use plugins, so is verry easy to configure.

Thanks for the link, but I tried that one already and I get absolutely no response at all... it just doesn't load anything unfortunately for some reason. :(

---

### Post by hessiess on 2008-09-28
> **xeriouxi said:**
> Thanks for the link, but I tried that one already and I get absolutely no response at all... it just doesn't load anything unfortunately for some reason. :(

strange... I needed to install a dependency, but besides that its been flawless.

will the emulator run, and not load roms, or just wont run?
have you put the bios in the 'bios' directory?
are you using a 64 bit OS?(if so you need to install the 32 bit libs).

can you try:

```
cd /path/containing/pSX/bin
./pSX
```

---

### Post by xeriouxi on 2008-09-29
> **hessiess said:**
> strange... I needed to install a dependency, but besides that its been flawless.

will the emulator run, and not load roms, or just wont run?
have you put the bios in the 'bios' directory?
are you using a 64 bit OS?(if so you need to install the 32 bit libs).

can you try:

```
cd /path/containing/pSX/bin
./pSX
```

Aha! I didn't have that said dependancy installed for some reason... works fine now! Thanks very much for your assistance! =)

---

