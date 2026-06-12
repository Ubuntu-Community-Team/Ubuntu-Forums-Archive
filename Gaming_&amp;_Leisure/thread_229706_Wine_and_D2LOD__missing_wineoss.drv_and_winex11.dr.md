---
title: "Wine and D2:LOD : missing wineoss.drv and winex11.drv -- where to find?"
date: 2006-08-04
forum: Gaming &amp; Leisure
---

### Post by chickengirl on 2006-08-04
I've copied my Diablo II folder over from my Windows drive and downloaded a cracked Diablo II.exe (because I can't get wine to recognize that the CD is in the drive)

I tried running the cracked exe and got this:

```
cassie@badger:~/.wine/drive_c/Program Files/D2LOD$ wine Diablo\ II.exe
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\psapi.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\midimap.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\msacm32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\msacm32.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\wineoss.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\dsound.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\uxtheme.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\imm32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\winex11.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\lz32.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\winspool.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\iphlpapi.dll
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\ole32.dll
```

So I copied over a bunch of the DLLs it was looking for from my windows drive, but a couple of them weren't there -- they seem to be wine related:

```
cassie@badger:~/.wine/drive_c/Program Files/D2LOD$ wine Diablo\ II.exe
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\wineoss.drv
fixme:dbghelp:SymLoadModule Should have successfully loaded debug information for image c:\windows\system32\winex11.drv
```

Does anyone know where to find those? If I'm barking up the wrong tree and there's an easier way to do this, please let me know.

---

