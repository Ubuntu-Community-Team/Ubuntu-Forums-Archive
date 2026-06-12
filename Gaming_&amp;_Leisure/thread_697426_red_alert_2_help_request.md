---
title: "red alert 2 help request"
date: 2008-02-15
forum: Gaming &amp; Leisure
---

### Post by harvodan on 2008-02-15
Hi all, I'm using wine 0.9.52, and I cannot install red alert 2. On the red alert 2 page on wine hq's appdb, a gold rating is given, and no mention is made of any problem with installing the game. I myself had it working a short time ago, but nothing at all seems to work. I've tried various versions of wine, different wine prefixes and running autorun.exe and setup.exe from the command line and by using the gui, but I do not get any results at all.

Here is the output from an attempt to run autorun.exe.

sirbubbles@sirbubbles-desktop:/media/cdrom0$ wine AUTORUN.EXE 
fixme:ntdll:NtFsControlFile stub! return success - Unsupported fsctl 90018 (device=9 access=0 func=6 method=0)
fixme:ntdll:NtFsControlFile stub! return success - Unsupported fsctl 9001c (device=9 access=0 func=7 method=0)
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:ntdll:NtFsControlFile stub! return success - Unsupported fsctl 90018 (device=9 access=0 func=6 method=0)
fixme:ntdll:NtFsControlFile stub! return success - Unsupported fsctl 9001c (device=9 access=0 func=7 method=0)
sirbubbles@sirbubbles-desktop:/media/cdrom0$ 

When running Setup.exe, it makes mention of SecDrv failing to load. Here is the output.

sirbubbles@sirbubbles-desktop:/media/cdrom0$ wine Setup.exe 
fixme:ntoskrnl:KeInitializeSpinLock 0x5777a4
err:winedevice:ServiceMain driver L"SecDrv" failed to load
fixme:spoolsv:serv_main (0 (nil))
SecuROM User Access Service (V7) 

UserAccess7 -install          to install the service
UserAccess7 -remove           to remove the service


starting service (may take some seconds)...sirbubbles@sirbubbles-desktop:/media/cdrom0$ err:winedevice:ServiceMain driver L"Secdrv" failed to load

btw, I'm using a wineprefix with no dll overrides of any kind.

Thanks, sorry for the long post.

---

### Post by harvodan on 2008-02-17
bump

---

