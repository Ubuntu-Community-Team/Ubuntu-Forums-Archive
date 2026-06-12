---
title: "copying files for steam"
date: 2005-11-19
forum: Gaming &amp; Leisure
---

### Post by immoral giant on 2005-11-19
This is probably a stupid question, but how to do i copy files from the desktop to ./wine/drive_c/Program\ Files/

I have wine installed fine, but i need to copy over the dll files.

---

### Post by invalid on 2005-11-19
```
cp ~/Desktop/*.dll ./wine/drive_c/Program\ Files/
```

Cheers,
Cb

---

### Post by immoral giant on 2005-11-19
i have copied over the files, but it doesn't seem to want to get past the loging on screen.

It just seems to hang and come up with this in the terminal:

```
fixme:vxd:VXD_Open Unknown/unsupported VxD L"gdperf.vxd". Try setting Windows version to 'nt40' or 'win31'.
err:module:import_dll Library MSVCR70.dll (which is needed by L"Z:\\home\\james\\.wine\\drive_c\\Program Files\\Steam\\CSERHelper.dll") not found
err:module:import_dll Library MSVCR70.dll (which is needed by L"Z:\\home\\james\\.wine\\drive_c\\Program Files\\Steam\\CSERHelper.dll") not found
Win32 MiniDump Helper version 1.0.0.0 (c) Copyright 2000-2003 Valve Corporation All rights reserved.

Expected argument 'ProcessId'.

Usage: WriteMiniDump [@argfile] [/?|h|help] [/v|version] [/Type <value>] <ProcessId> <DumpFile>

@argfile        Read arguments from a file.
/?              Show usage.
/v              Show version.
/Type <value>   Select dump type values are:
                   normal
                   full
ProcessId       Select process id for which to generate a dump
DumpFile        Select path of output dump file




```

I have put the MSVCR70.dll file into the windows\system folder, which i think is the right one. and have done regsvr32 /s MSVCR70.dll on it.

What do I have to do??
I just want to play CSS. :mad:

---

### Post by YokoZar on 2005-11-20
[QUOTE=immoral giant]This is probably a stupid question, but how to do i copy files from the desktop to ./wine/drive_c/Program\ Files/

I have wine installed fine, but i need to copy over the dll files.[/QUOTE]
Remember that ~/.wine is a hidden directory - you'll have to have nautilus set to show hidden folders.  "./wine" is wrong.

Are you sure you copied files into the right place?

Also, I advise following the howto here: [http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)

---

### Post by immoral giant on 2005-11-27
I've tried following that guide but i get nowhere.  I follow everything through, but steam either doesn't run, or it updates really really slowly.

---

