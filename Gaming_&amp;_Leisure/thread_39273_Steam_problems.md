---
title: "Steam problems"
date: 2005-06-04
forum: Gaming &amp; Leisure
---

### Post by sabelsatan on 2005-06-04
When I try to run Steam wit Cedega from CVS (I used tehe script from linux-gamers.net), I get the following error:

[email]sabelsatan@sabelsatan:~/.cvsc[/email]edega/c_drive/Spill/Steam$ cvscedega STEAM.exe
Warning: Language 'en_NO' was not found, retrying without country name...
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:Fontconfig_Init Fontconfig support was not compiled in at compile time.
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
fixme:keyboard:X11DRV_KEYBOARD_DetectLayout Your keyboard layout was not found!
Using closest match instead (Norwegian keyboard layout) for scancode mapping.
Please define your layout in windows/x11drv/keyboard.c and submit them
to us for inclusion into future Wine releases.
See the Wine User Guide, chapter "Keyboard" for more information.
err:task:GetThreadQueue16 Breaking 16 bit for tid 2
err:task:GetThreadQueue16 Breaking 16 bit for tid 2
fixme:ntdll:NtQueryInformationProcess (0xffffffff,0x00000000,0xb78ee9dc,0x00000018,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001d4,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001e4,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x00000204,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x00000208,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x0000020c,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x00000210,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x00000214,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x00000218,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x0000021c,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x00000220,0x00000000,0xb78ee6d8,0x0000001c,(nil)),stub!
fixme:psapi:EnumProcessModules (hProcess=0xffffffff, 0xb78eea64, 2048, 0xb78ef6b0): stub
fixme:ver:GetVersionExA OSVERSIONINFOA is too large (possibly OSVERSIONINFOEXA)
/home/sabelsatan/bin/cvscedega: line 87: 13999 Segmentation fault      "$ConfigurePrefix/bin/$WineExecName" "$@"
[email]sabelsatan@sabelsatan:~/.cvsc[/email]edega/c_drive/Spill/Steam$

---

