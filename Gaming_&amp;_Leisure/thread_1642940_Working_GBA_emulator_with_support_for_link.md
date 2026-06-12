---
title: "Working GBA emulator with support for link?"
date: 2010-12-11
forum: Gaming &amp; Leisure
---

### Post by Minkovsky on 2010-12-11
So I'm looking for a GBA emulator with support for link, be it single-pc or multi-pc link. Also, if you want, you may just tell me how to recompile VBA-1.7.2 with link files from VBA-link sources? Thanks...
PS. Link will be used for trading pokemon around.

---

### Post by Minkovsky on 2010-12-13
hello?

---

### Post by Minkovsky on 2010-12-21
bump

---

### Post by DangerOnTheRanger on 2010-12-21
I'm all over it!
```

Package: mednafen
Priority: optional
Section: universe/games
Installed-Size: 5664
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Ryan Schultz <schultz.ryan@gmail.com>
Architecture: i386
Version: 0.8.C-0ubuntu2
Depends: libasound2 (>> 1.0.22), libc6 (>= 2.7), libcdio10, libgcc1 (>= 1:4.1.1), libsdl-net1.2, libsdl1.2debian (>= 1.2.10-1), libsndfile1 (>= 1.0.20), libstdc++6 (>= 4.1.1), zlib1g (>= 1:1.1.4)
Filename: pool/universe/m/mednafen/mednafen_0.8.C-0ubuntu2_i386.deb
Size: 1932816
MD5sum: 6b0a75072e2d0110960686098b015bfb
SHA1: ba7807f884f2f8fb7a14432ae170a3d7aa7f6acf
SHA256: 5468f24e0a18a8eb954f938609d0c439aed8abb0ef61e39f9a4ed8ba475bb3c6
Description: multi-platform emulator, including NES, GB/A, Lynx, PC Engine
 Mednafen is a command-line driven emulator for many different systems. It
 has full support for OpenGL and SDL graphics, network play, remappable input
 configuration, joystick and keyboard support, save states, game rewinding,
 GSF playback, and screenshots.
 .
 The systems supported by Mednafen are:
    * Atari Lynx
    * GameBoy
    * GameBoy Color
    * GameBoy Advance
    * NES
    * PC Engine (TurboGrafx 16)
    * PC-FX
    * SuperGrafx
    * NeoGeo Pocket, NeoGeo Pocket Color
    * WonderSwan
 .
 Hardware emulated by Mednafen includes:
    * NES gamepad, Zapper, PowerPad
    * Four-Score, Famicom multiplayer adapter
    * Arkanoid, HyperShot, Space Shadow, Mahjong controllers
    * Oeka Kids tablet, Quiz King buzzers, Family Trainer, Barcode World
    * Game Genie
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

```That emulator (installable from the repos) should work. But I really think you should do a little more work before posting; I found that in 30 seconds, with a simple **apt-cache search game boy**.

---

### Post by seanm0447 on 2011-04-02
How exactly to you set to run mednafen? It isn't listed under Games. It says it command driven or of sort. When I typed in mednafen into the command line it gave me this:
> mednafen
Starting Mednafen 0.8.C
 Loading settings from "/home/sean/.mednafen/mednafen.cfg"...Failed: No such file or directory
 Compiled against SDL 1.2.14, running with SDL 1.2.14

No command-line arguments specified.

Usage: mednafen [OPTION]... [FILE]
    Please refer to the documentation for option parameters and usage.

---

### Post by Dlambert on 2011-04-02
Visual Boy Advance

---

### Post by DoktorSeven on 2011-04-02
> **seanm0447 said:**
> How exactly to you set to run mednafen? It isn't listed under Games. It says it command driven or of sort. When I typed in mednafen into the command line it gave me this:

Mednafen frontend:
[http://ubuntuforums.org/showthread.php?t=813785](http://ubuntuforums.org/showthread.php?t=813785)

Or failing that, just enter the path to a ROM from the commandline:

**mednafen /path/to/your/gba/roms/gbarom.zip**

(of course, you use the actual path and romname , not my fake path/romname there)

Network play documentation: [http://mednafen.sourceforge.net/documentation/netplay.html](http://mednafen.sourceforge.net/documentation/netplay.html)

---

