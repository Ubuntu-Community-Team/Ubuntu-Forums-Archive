---
title: "dolphin-emu segfault"
date: 2010-12-22
forum: Gaming &amp; Leisure
---

### Post by Super Goombario on 2010-12-22
I can start dolphin-emu just fine. I start up a game, and just as the game gets started (before it actually shows anything but I know it's starting because the speed drops), the window closes. When I run from the terminal, I get this:

```
24:16:600 /build/buildd/dolphin-emu-2.0+svn6580/Source/Core/Common/Src/FileUtil.cpp:98 W[COMMON]: IsDirectory: stat failed on /home/joseph/.dolphin-emu/Wii/title/00000001/00000002/content: 
24:16:787 /build/buildd/dolphin-emu-2.0+svn6580/Source/Core/DolphinWX/Src/X11Utils.cpp:147 N[Video]: XRRExtension-Version 1.3
24:16:807 /build/buildd/dolphin-emu-2.0+svn6580/Source/Core/DolphinWX/Src/X11Utils.cpp:189 N[Video]: Fullscreen Resolution 640x480
24:18:681 /build/buildd/dolphin-emu-2.0+svn6580/Source/Plugins/Plugin_VideoOGL/Src/GLUtil.cpp:351 N[Video]: glX-Version 1.2
24:18:681 /build/buildd/dolphin-emu-2.0+svn6580/Source/Plugins/Plugin_VideoOGL/Src/GLUtil.cpp:373 N[Video]: Got Doublebuffered Visual!
24:19:014 /build/buildd/dolphin-emu-2.0+svn6580/Source/Core/Core/Src/Boot/Boot.cpp:165 N[BOOT]: Booting /home/joseph/Games/ROMs/GCN/xxxxxx.iso
24:19:038 /build/buildd/dolphin-emu-2.0+svn6580/Source/Core/DiscIO/Src/FileMonitor.cpp:135 N[FileMon]: Opening '/home/joseph/Games/ROMs/GCN/xxxxxx.iso'
24:19:094 /build/buildd/dolphin-emu-2.0+svn6580/Source/Core/Core/Src/HLE/HLE_OS.cpp:52 N[OSREPORT]: 81200500->81300000| Apploader Initialized.  $Revision: 31 $.
24:19:094 /build/buildd/dolphin-emu-2.0+svn6580/Source/Core/Core/Src/HLE/HLE_OS.cpp:52 N[OSREPORT]: 8120051c->81300000| This Apploader built Sep  5 2002 05:58:53
Allocating 1024 x 1024 radeon RBO (pitch 1024)
24:19:462 /build/buildd/dolphin-emu-2.0+svn6580/Source/Core/Core/Src/PowerPC/Interpreter/Interpreter_SystemRegisters.cpp:353 N[PowerPC]: Flush Instruction Cache! ICE=0
24:19:518 /build/buildd/dolphin-emu-2.0+svn6580/Source/Core/Core/Src/PowerPC/Interpreter/Interpreter_SystemRegisters.cpp:344 N[PowerPC]: Instruction Cache Enable (HID0.ICE) = 1
24:19:806 /build/buildd/dolphin-emu-2.0+svn6580/Source/Core/AudioCommon/Src/AlsaSoundStream.cpp:186 N[Audio]: ALSA gave us a 8192 sample "hardware" buffer with 32 periods. Will send 256 samples per fragments.

24:19:813 /build/buildd/dolphin-emu-2.0+svn6580/Source/Core/AudioCommon/Src/AlsaSoundStream.cpp:217 N[Audio]: ALSA successfully initialized.

Segmentation fault
```

I don't think updating would help because I just reformatted, so the earliest I could have installed dolphin was last Friday (December 17th, 2010).

Specifications:
Ubuntu 10.04 LTS 64-bit Desktop Edition
Dell Studio 1535 Laptop
Intel Core2Duo 2.0ghz
3.9GB RAM
223.6GB HD
ATi Mobility Radeon HD4500 512mb VRAM

I might not be capable of running dolphin smoothly but I'd just like to run the game, at 10fps if I have to.

---

### Post by thatguruguy on 2010-12-22
Does this happen for every game?  Is it a game that is supposed to work well with dolphin-emu?

---

### Post by Super Goombario on 2010-12-22
The game I'm trying to emulate (wind waker) is supposed to work pretty well. People with computers [less competent than mine were able to run it at 10-15 fps.](http://forums.dolphin-emulator.com/showthread.php?tid=40&pid=111750#pid111750)

I haven't done much gamecube emulation since my switch to ubuntu (and I won't do wii emulation at all until I get a bluetooth device), so I don't really know if it's every game. I know for sure that I tried a game that does not work in dolphin (mgs: twin snakes) and it closed out the same way on me, I can't say for sure if it was an incompatibility problem or this same issue.

My interest in running gamecube games is solely for the purpose of playing games I used to own that don't work anymore. I really want to play twilight princess but I wanted to start out with something less demanding first (ww).

---

### Post by Super Goombario on 2011-01-31
I've discovered the issue: I didn't install the proprietary drivers for my video card. It works fine. If you're getting this problem, remember to install proprietary drivers for your video (and possibly sound) card.

---

