---
title: "WoW Using cvscedega/Existing Windows install"
date: 2006-05-07
forum: Gaming &amp; Leisure
---

### Post by Kerris on 2006-05-07
I've installed World of Warcraft on an existing (real) Windows XP installation (dual-booting).  I would like to see if I can get it running under either wine or cvscedega.  I've been able to edit the cvscedega config file to get rid of most of the dll errors, but I'm still getting one, as well as some "fixme" errors.  Here is the output:

> cedega WoW.exe --debugmsg +err --debugmsg +warn
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
err:win32:PE_fixup_imports No implementation for ADVAPI32.dll.563(SetSecurityInfo) imported from C:\World of Warcraft\WoW.exe, setting to 0xdeadbeef
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
Warning: Language 'us' was not recognized, defaulting to English
wine: Unhandled exception, starting debugger...
err:win:GetDesktopWindow Wine init error: either you're trying to use an invalid native USER.EXE config, or some graphics/GUI libraries or DLLs didn't initialize properly. Aborting.

I've looked around on Google, and the transgaming forums, and have found nothing helpful.  Any suggestions?

---

