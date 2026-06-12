---
title: "Trouble Using Steam with CedegaCVS"
date: 2005-08-11
forum: Gaming &amp; Leisure
---

### Post by Zachs23 on 2005-08-11
hi, I have been having trouble getting steam to work with Cedega (CVS version). The install went perfectly, and I downloaded a few dll's that a how-to on linux-gamers.net said were required. The first time (after install) it ran and updated, but closed unexpectedly. i have tried cd-ing into the directory of steam.exe first, then 'cvscedega Steam.exe" When I do, it either does not launch at all, or launches for a second then closes, with this error in the console (a bit long):
```
zach@ubuntu:~$ cd /home/zach/.cvscedega/c_drive/ProgramFiles/Valve/Steam/
zach@ubuntu:~/.cvscedega/c_drive/ProgramFiles/Valve/Steam$ cvscedega Steam.exe
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
err:task:GetThreadQueue16 Breaking 16 bit for tid 2
err:task:GetThreadQueue16 Breaking 16 bit for tid 2
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:DEVICE_Open Unknown/unsupported VxD GDPERF. Try --winver nt40 or win31 !
fixme:ver:GetVersionExA OSVERSIONINFOA is too large (possibly OSVERSIONINFOEXA)
fixme:ntdll:NtQueryInformationProcess (0xffffffff,0x00000000,0xb78ee9dc,0x00000018,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001e0,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001e4,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001e8,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001ec,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001f0,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001f4,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001f8,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001fc,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x00000200,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x00000204,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:psapi:EnumProcessModules (hProcess=0xffffffff, 0xb78eea64, 2048, 0xb78ef6b0): stub
fixme:ver:GetVersionExA OSVERSIONINFOA is too large (possibly OSVERSIONINFOEXA)
/usr/bin/cvscedega: line 87: 14629 Segmentation fault      "$ConfigurePrefix/bin/$WineExecName" "$@"
```

Can someone who knows a bit more about this let me know what it means?
Thanks a lot
P.S. I am running a Sony Vaio with Radeon IGP345M video card. I dont think this is a hardware issue, if so, I will give more hardware info.
Thanks again

---

### Post by anacron on 2005-08-12
well I don't know much about getting cvs work, but there seems to be issue with alsa and truetype font's for an example. So try to do something for those at first, there should be good tutorial how to get alsa work in hoary and that truetype thing can be found also (you might get it with synaptic just with name like that) also, have you tryed to install wine? installing wine-tools might help

---

### Post by patrick295767 on 2006-07-20
Concerning installations, I might be quoting the msi and dcom 98 links from linux gamers:

To play HL2 for instance, you'll need MSI Microsoft Installers(Installshield/MSI );) 


> Issue:

No 3D accleration with ATI in games



Solution:

$ export LD_PRELOAD=/usr/lib/libGL.so; cvscedega game.exe




--------------------------------------------------------------------------------



Issue:

err:font:WineEngInit FreeType support is not compiled in to wine, some font functionality will be disabled.


Solution:

Install Fontconfig, Freetype2 (libfreetype6) and Freetype2-devel


Here are some more hints about Cedega and Installshield/MSI installers from [http://www.frankscorner.org](http://www.frankscorner.org)



The CVS version of Cedega has no support for Installshield installers, but a lot of games use this installer. To make installation possible you must install the DCOM98 utility.



[B]You can download DCOM98 here:
[http://www.microsoft.com/com/dcom/dcom98/download.asp](http://www.microsoft.com/com/dcom/dcom98/download.asp)
Type $ cvscedega dcom98.exe to install DCOM98.[/B]



**To install .msi (Microsoft Installer) files get [http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe](http://download.microsoft.com/download/WindowsInstaller/Install/2.0/W9XMe/EN-US/InstMsiA.exe) and install it with the command You can install Windows Installer by typing $ cvscedega instmsia.exe Now type $ cvscedega msiexec /i somefile.msi and the application will be installed.**


---

### Post by patrick295767 on 2006-07-20
(Aaaand sh?t !!
Sorry for this old thread.)

---

