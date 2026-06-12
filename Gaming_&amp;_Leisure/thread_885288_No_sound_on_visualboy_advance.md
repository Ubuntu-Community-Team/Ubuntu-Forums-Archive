---
title: "No sound on visualboy advance"
date: 2008-08-09
forum: Gaming &amp; Leisure
---

### Post by ukyo_rulz on 2008-08-09
I installed Ubuntu Hardy on my sister's Acer Aspire 6920 a couple of months ago and it's been working fine. I had to install special drivers for the wired net connection and the sound, but after that it was smooth sailing.

Until today, when my sister installed visualboy advance to play some games. There's no sound at all, and the game runs at very high speeds (may be related to sound problem?). Anyway, I was wondering if the fact that I had to manually install OSS sound drivers may be the culprit. The same problem cropped up when I set up mplayer and amarok for her, but I fixed those problems by setting the sound to OSS. I can find no such option on the cfg file of visualboy, or the gui (vba express) that came with it. Any help would be appreciated.

---

### Post by FranMichaels on 2008-08-10
I would recommend [mednafen]("http://mednafen.sourceforge.net/"). Its gba emulation code is based on visual boy advance, and it's quite good all around. It is in the repos, and you can set OSS as the sound output if you need to.

After launching, the config is in ~/.mednafen/mednafen.cfg

The emulator itself is easy, just press F1 for the hotkeys to map the gamepad, and just choose open with so you can double click the game to launch it. If you prefer a gui front-end, [http://ubuntuforums.org/showthread.php?t=813785](http://ubuntuforums.org/showthread.php?t=813785)

---

### Post by ukyo_rulz on 2008-08-10
I installed mednafen through synaptic and it worked like a charm. Many thanks!

---

