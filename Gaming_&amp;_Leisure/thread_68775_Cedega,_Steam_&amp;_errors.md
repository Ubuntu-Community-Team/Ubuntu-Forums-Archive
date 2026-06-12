---
title: "Cedega, Steam &amp; errors"
date: 2005-09-24
forum: Gaming &amp; Leisure
---

### Post by rama on 2005-09-24
I have successfully installed cvscedega (got the code, comiled it etc).
I am trying to make steam work and although the installation **seems** to work fine i get a number of errors when the application attempts to start.

This is the output during the installation. 
```

user@computer:~/bin$ ./cvscedega /home/jsar/.cvscedega/drive_c/Valve/Condition\ Zero/steaminstall.exe
Warning: Language 'en_GR' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
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
err:module:MODULE_LoadLibraryExA Loading of native DLL C:\Valve\Steam\UNWISE.INI failed, check this file ! (GetLastError 193)
fixme:ole:CoCreateInstance no classfactory created for CLSID {00021401-0000-0000-c000-000000000046}, hres is 0x80040154
fixme:ole:CoCreateInstance no classfactory created for CLSID {00021401-0000-0000-c000-000000000046}, hres is 0x80040154
fixme:ole:CoCreateInstance no classfactory created for CLSID {00021401-0000-0000-c000-000000000046}, hres is 0x80040154
fixme:ole:CoCreateInstance no classfactory created for CLSID {00021401-0000-0000-c000-000000000046}, hres is 0x80040154
/home/jsar/.WineCVS/installs/cvscedega/bin/wine: binary overlaps reserved area 
(08048000-0804ca5c)
err:file:DeleteFileA Empty path passed
user@computer:~/bin$ Warning: Language 'en_GR' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:task:GetThreadQueue16 Breaking 16 bit for tid 5
err:task:GetThreadQueue16 Breaking 16 bit for tid 5
fixme:module:CreateProcessA (C:\Valve\Steam\STEAMTmp.exe,...): 
NORMAL_PRIORITY_CLASS ignored
/home/user/.WineCVS/installs/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804ca5c)
Warning: Language 'en_GR' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:task:GetThreadQueue16 Breaking 16 bit for tid 8
fixme:module:CreateProcessA (C:\Valve\Steam\STEAM.exe,...): NORMAL_PRIORITY_CLASS 
ignored
/home/user/.WineCVS/installs/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804ca5c)
Warning: Language 'en_GR' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:task:GetThreadQueue16 Breaking 16 bit for tid 5
err:task:GetThreadQueue16 Breaking 16 bit for tid 5
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

```

---

### Post by rama on 2005-09-24
```

fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:DEVICE_Open Unknown/unsupported VxD GDPERF.VXD. Try --winver nt40 or win31 !
fixme:ver:GetVersionExA OSVERSIONINFOA is too large (possibly OSVERSIONINFOEXA)
fixme:winsock:WS_bind Setting WS_SO_REUSEADDR on socket before we binding it
fixme:ole:CoCreateInstance no classfactory created for CLSID {8856f961-340a-11d0-a96b-00c04fd705a2}, hres is 0x80040154
/home/user/.WineCVS/installs/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804ca5c)
Warning: Language 'en_GR' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
fixme:psapi:GetModuleBaseNameW (hProcess=0xffffffff, hModule=0xb40cd000, L"", 2034): stub
err:msvcrt:MSVCRT_Init TLS free failed! error = 0
err:msvcrt:MSVCRT_Init TLS free failed! error = 0
Shutting down. . .
30err:msvcrt:MSVCRT_Init TLS free failed! error = 0
err:msvcrt:MSVCRT_Init TLS free failed! error = 0
err:msvcrt:MSVCRT_Init TLS free failed! error = 0
err:msvcrt:MSVCRT_Init TLS free failed! error = 0
err:msvcrt:MSVCRT_Init TLS free failed! error = 0
wine: Unhandled exception, starting debugger...



I am living in greece thus the language warnings. It also appears that cedega has some kind of problem with alsa, although I never had any problems with other apps that use it.
When the installation terminates I get a msgbox from steam with the following message: 

*Steam.exe (main exception):Win32 StructuredException at B4479729 : Attempt to write to virtual address 3520528629 without appropriate access rights.*
At this point I can see that I have a sleeping process running steam.exe via wine.

If I try to execute steam.exe again I get this:

[CODE]
user@computer:~/bin$ ./cvscedega ~/.cvscedega/drive_c/Valve/Steam/Steam.exe Warning: Language 'en_GR' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:task:GetThreadQueue16 Breaking 16 bit for tid 2
user@computer:~/bin$

``` 
I also get a msgbox from steam :
*Steam.exe (main exception):Unable to change directory to /home/user/.cvscedega/drive_c/Valve/Steam/*

The directory obviously exists.

Any ideas? Could it be something in any of the cedega config/profile files?

---

### Post by strikeforce on 2005-09-24
Its missing pthreads which I'm not sure if its needed or not but its generating an error because of that.

Only reason I know that is because someone in the transgaming forums asked the exact same question :)

---

### Post by rama on 2005-09-24
[QUOTE=strikeforce]Its missing pthreads which I'm not sure if its needed or not but its generating an error because of that.

Only reason I know that is because someone in the transgaming forums asked the exact same question :)[/QUOTE]
 So what can I do about it?
I found this in another thread about steam :
[http://downloads.transgaming.com/files/cedega-4.4.1_releasenotes.html#steam](http://downloads.transgaming.com/files/cedega-4.4.1_releasenotes.html#steam)
The second bullet is exactly what I am dealing with. So where do I add the "-use-pthreads on" parameter?
I use the following command to start steaminstall.exe :
cvscedega steaminstall.exe

---

