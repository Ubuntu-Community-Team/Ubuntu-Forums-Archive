---
title: "Corrupt files in WoW"
date: 2007-09-10
forum: Gaming &amp; Leisure
---

### Post by know1.2 on 2007-09-10
Thanks to Sammi's excellent HOW-TO, I've gotten WoW up and running under Wine with good FPS and nice graphics.

Sadly, I've been plagued with a really frustrating error. After some random period of time, from 10 minutes to days of play, Warcraft bombs out with the following error:

------------------------------------------------------------------------------
This application has encountered a critical error:

ERROR #131 (0x85100083) File Corrupt
Program: C:\Program Files\World of Warcraft\WoW.exe
File: Data\common.MPQ

File = Sound\Ambience\WMOAmbience\IronforgeTheGreatForge. wav
Cached Read = Decompression failed
Raw Read = Decompression failed

WoWBuild: 6898
------------------------------------------------------------------------------

However, the file that it's trying to pull out of the 'common.MPQ' changes. If I've done the little fix I have below it's different, but if I get this error and try to relaunch it'll bomb out on me again with the identical error.

A 'work around' I have in place was to completely reinstall the application and fully patch the whole thing. After getting everything up to the latest levels I made a copy of the whole World of Warcraft directory (copied from ~/.wine/drive_c/Program Files/World of Warcraft) to another place on my hard disc. Then when I get this error, I pull out my fresh copy of common.mpq and copy it back over the corrupted one in my wine directory. This also works for patch-2.mpq which has corrupted on my a couple times.

I'm running Feisty Fawn (7.04) on an HP Pavillion 6428CA. Dual core AMD 64 with Nvidia GO 6150.

Linux mako 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64 GNU/Linux

Wine 0.9.43 AMD version from repository.

If anybody has any thoughts or the same problem, I'd love to hear!

know1

---

