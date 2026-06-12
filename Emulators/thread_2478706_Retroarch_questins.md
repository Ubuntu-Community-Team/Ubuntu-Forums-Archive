---
title: "Retroarch questins"
date: 2022-09-02
forum: Emulators
---

### Post by jonfisher on 2022-09-02
I installed Retroarch; however, upon launching it, I'm unable to click on anything to get something to work.  So in terminal I used "xkill" to exit it.

Question #2.  I'm trying to install the Atari 7800 emulator into Retroarch (using [https://www.howtoretro.com/what-is-the-best-atari-7800-emulator/#What_Is_The_Best_Atari_7800_Emulator_For_PC_Mac_Linux](https://www.howtoretro.com/what-is-the-best-atari-7800-emulator/#What_Is_The_Best_Atari_7800_Emulator_For_PC_Mac_Linux))

Once I get retroarch responding, any tips on what to do it get it installed into Retroarch  (I downloaded [a7800-linux-v5.2.tgz]("https://github.com/7800-devtools/a7800/releases/download/v5.2/a7800-linux-v5.2.tgz") from [https://github.com/7800-devtools/a7800/releases](https://github.com/7800-devtools/a7800/releases))


much thanks for any help....


Addendum:  This appears to be the same retroarch problem I'm experiencing:  [https://github.com/libretro/RetroArch/issues/5151](https://github.com/libretro/RetroArch/issues/5151)

---

### Post by Holger_Gehrke on 2022-09-12
The a7800 is a stand-alone emulator. It neither needs nor wants Retroarch (which doesn't necessarily mean you can't get retroarch to start it, only that it's not necessary). It's based on the Atari 7800 core of MAME, which explains why it looks and behaves the way it does. The .tgz file you downloaded is a .tar.gz and can be unpacked with 'tar -xzf a7800-linux-v5.2.tgz'. After that you will have a directory named a7800-linux that has the emulator (a7800), a manual in PDF-format, and several directories with other stuff.

Holger

---

