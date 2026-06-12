---
title: "VBA running at ridiculous speeds"
date: 2008-10-25
forum: Gaming &amp; Leisure
---

### Post by SeriousName on 2008-10-25
So this is bizarre.

Yesterday VBA Express was working fine for me, but when I started it up today games are running with no sound at speeds of around 400%. I hadn't altered any settings, though I have tried a number of changes since this started and none have made a difference.

I've also tried running VBA from the command line. It runs even faster (1000+%), although that may be because I'm not including all the settings VBA Express uses.

I don't have any idea what could have caused this. The only related thing I can think of is that yesterday when I tried to run Gens (as found in [this thread]("http://ubuntuforums.org/showthread.php?t=290008")) the sound wasn't working, and in fact it failed the SDL sound test in the options menu.

---

### Post by Sockerdrickan on 2008-10-25
VBA for Linux is weird, use VBA-M (or TuxBoy if it's a GB/C game [www.tuxemu.se.nu](www.tuxemu.se.nu))

---

### Post by SeriousName on 2008-10-26
TuxBoy won't do, and I really don't want to have to compile VBA-M from source code.

I've got some idea what the problem is now. On a hunch, I switched out the standard SDL library with OSS for the one with ALSA. Now there is sound, but it's horribly garbled. Also, the emulator is running a bit fast at about 108%, which is acceptable if annoying. Still, I want to get VBA running as well as it was before.

Also, using the SDL with ALSA, Gens works fine again; no garbled sound like VBA.

---

### Post by SeriousName on 2008-10-26
Okay, it seems I've solved my own problem. I figured it had to have something to do with sound, so I ended up simply upgrading to OSS4 using [this guide](https://help.ubuntu.com/community/OpenSound), and now everything works just as well as before.

---

