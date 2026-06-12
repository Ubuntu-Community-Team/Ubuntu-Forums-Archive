---
title: "Errors with Cedega, still trying! :)"
date: 2005-09-10
forum: Gaming &amp; Leisure
---

### Post by Statik on 2005-09-10
Hi all,

I finally got cvscedega to install and run on my install. I even fixed the font problem, however, I'm still getting errors. Here's the output when I try to install Html-Kit, an editor I use:
> 
fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
/home/statik/.WineCVS/installs/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804ca1c)
fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0081
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0083
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0001
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0005
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0003
fixme:richedit:RICHED20_WindowProc Unhandled message 0xbe10
fixme:richedit:RICHED20_WindowProc Unhandled message 0x000c
fixme:richedit:RICHED20_WindowProc Unhandled message 0x043b (WM_USER + 59)
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0445 (WM_USER + 69)
fixme:richedit:RICHED20_WindowProc Unhandled message 0x045b (WM_USER + 91)
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0030
fixme:richedit:RICHED20_WindowProc Unhandled message 0x00c5
fixme:richedit:RICHED20_WindowProc Unhandled message 0x00b9
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0046
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0047
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0435 (WM_USER + 53)
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0449 (WM_USER + 73)
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0046
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0047
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0007
fixme:richedit:RICHED20_WindowProc Unhandled message 0xb029
fixme:richedit:RICHED20_WindowProc Unhandled message 0x000f
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0085
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0008
err:progress:ProgressWindowProc unknown msg be10 wp=660001 lp=00010066
fixme:richedit:RICHED20_WindowProc Unhandled message 0x000e
fixme:richedit:RICHED20_WindowProc Unhandled message 0x00b8
fixme:richedit:RICHED20_WindowProc Unhandled message 0x000e
fixme:richedit:RICHED20_WindowProc Unhandled message 0xbe10
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0018
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0046
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0047
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0002
fixme:richedit:RICHED20_WindowProc Unhandled message 0x0082 

Now, the CDRom part, I don't understand how to fix it, but I know where it is at least. The section in my config reads:
> [Drive F]
"Path" = "/media/cdrom"
"Type" = "cdrom"
"Label" = "CD-ROM"
"Filesystem" = "win95"
"Device" = "/dev/hdc"  

Other than that, I'm lost. Anyone know what I'm supposed to do to fix it?

Trying to install steam gives the following output, although Steam says it's installed.:
> fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
fixme:wave:ALSA_WaveInit -fixme:wave:ALSA_WaveInit -
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:richedit:RICHED32_WindowProc Unknown message 0x0081
fixme:richedit:RICHED32_WindowProc Unknown message 0x0210
fixme:richedit:RICHED32_WindowProc Unknown message 0x0030
fixme:richedit:RICHED32_WindowProc Unknown message 0x0087
fixme:richedit:RICHED32_WindowProc Unknown message 0x0030
ReadStyleSheet: missing style number
Last token read was "}" near line 2, position 22.
fixme:richedit:RICHED32_WindowProc Unknown message 0x0115
fixme:richedit:RICHED32_WindowProc Unknown message 0x0115
fixme:richedit:RICHED32_WindowProc Unknown message 0x0138
fixme:richedit:RICHED32_WindowProc Unknown message 0x0138
fixme:richedit:RICHED32_WindowProc Unknown message 0x0082
/home/statik/.WineCVS/installs/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804ca1c)
fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
err:file:DeleteFileA Empty path passed
err:task:GetThreadQueue16 Breaking 16 bit for tid 5
err:task:GetThreadQueue16 Breaking 16 bit for tid 5
fixme:module:CreateProcessA (C:\Program Files\Valve\Steam\STEAMTmp.exe,...): NORMAL_PRIORITY_CLASS ignored
/home/statik/.WineCVS/installs/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804ca1c)
fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
err:task:GetThreadQueue16 Breaking 16 bit for tid 9
fixme:module:CreateProcessA (C:\Program Files\Valve\Steam\STEAM.exe,...): NORMAL_PRIORITY_CLASS ignored
/home/statik/.WineCVS/installs/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804ca1c)
fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
err:task:GetThreadQueue16 Breaking 16 bit for tid 5
err:task:GetThreadQueue16 Breaking 16 bit for tid 5
fixme:wave:ALSA_WaveInit -fixme:wave:ALSA_WaveInit -
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:DEVICE_Open Unknown/unsupported VxD GDPERF.VXD. Try --winver nt40 or win31 !
fixme:ver:GetVersionExA OSVERSIONINFOA is too large (possibly OSVERSIONINFOEXA)
fixme:winsock:WS_bind Setting WS_SO_REUSEADDR on socket before we binding it
err:module:PE_fixup_imports Module (file) MSVCR70.dll (which is needed by C:\Program Files\Valve\Steam\CSERHelper.dll) not found
err:win32:PE_LoadLibraryExA can't load C:\Program Files\Valve\Steam\CSERHelper.dll
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\Program Files\Valve\Steam\CSERHelper.dll failed, check this file ! (GetLastError 14)
err:module:PE_fixup_imports Module (file) MSVCR70.dll (which is needed by C:\Program Files\Valve\Steam\CSERHelper.dll) not found
err:win32:PE_LoadLibraryExA can't load C:\Program Files\Valve\Steam\CSERHelper.dll
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\Program Files\Valve\Steam\CSERHelper.dll failed, check this file ! (GetLastError 14)
/home/statik/.WineCVS/installs/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804ca1c)
fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
err:msvcrt:MSVCRT_Init TLS free failed! error = 0
err:msvcrt:MSVCRT_Init TLS free failed! error = 0
err:msvcrt:MSVCRT_Init TLS free failed! error = 0
err:msvcrt:MSVCRT_Init TLS free failed! error = 0
err:msvcrt:MSVCRT_Init TLS free failed! error = 0
err:msvcrt:MSVCRT_Init TLS free failed! error = 0
err:msvcrt:MSVCRT_Init TLS free failed! error = 0
err:ntdll:display_wait_error Timeout. Retry with 60 secs: crit=0xad12593c name="?" ec=1 cc=1
err:ntdll:display_wait_error backtrace="0xb7f168f6,0xb7f163bf,0xb7f15c90,0xb7f15c05,0xb7f941af,0xad0623ba "
err:ntdll:display_wait_error   crit (0xad12593c): lc 1 rc 1 ot 15 sem 8 spin 0
wine: Unhandled exception, starting debugger...
tid 11639 received signal 15. Raising signal 3 

Same thing, how do I fix this?

Statik

---

### Post by arpunk on 2005-12-13
How did you fixed your font problems?

---

### Post by Statik on 2005-12-14
not yet. Gave up for a while so I can finish off exams and some other more pressing real life problems. Considering installing XP on a separate HD as a game install.

Statik

---

