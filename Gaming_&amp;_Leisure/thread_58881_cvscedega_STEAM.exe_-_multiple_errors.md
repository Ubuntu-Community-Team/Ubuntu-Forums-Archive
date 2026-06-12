---
title: "cvscedega STEAM.exe - multiple errors"
date: 2005-08-21
forum: Gaming &amp; Leisure
---

### Post by OneSeventeen on 2005-08-21
I just installed cvscedega and downloaded/ran the STEAM installer from steampowered.com

It seemed to be working fine, until it tried to udpate steam, then it told me only one instance of steam could run at a time (it did this on Windows too), so I ran the command again, and it looked like it was going to finish, but it errored out.  I tried running STEAM.exe again, and this is what I get:
```

oneseventeen@tigershark:~/.cvscedega/c_drive/Program Files/Valve/Steam$ cvscedega STEAM.exe
For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
err:task:GetThreadQueue16 Breaking 16 bit for tid 2
err:task:GetThreadQueue16 Breaking 16 bit for tid 2
err:module:BUILTIN_LoadModule loaded .so but dll winealsa.drv still not found
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
fixme:win32:DEVICE_Open Unknown/unsupported VxD GDPERF. Try --winver nt40 or win31 !
fixme:ver:GetVersionExA OSVERSIONINFOA is too large (possibly OSVERSIONINFOEXA)
fixme:ntdll:NtQueryInformationProcess (0xffffffff,0x00000000,0xb78fe9dc,0x00000018,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001e0,0x00000000,0xb78fe6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001e4,0x00000000,0xb78fe6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001e8,0x00000000,0xb78fe6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001ec,0x00000000,0xb78fe6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001f0,0x00000000,0xb78fe6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001f4,0x00000000,0xb78fe6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001f8,0x00000000,0xb78fe6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x000001fc,0x00000000,0xb78fe6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x00000200,0x00000000,0xb78fe6d8,0x0000001c,(nil)),stub!
fixme:ntdll:NtQueryInformationThread (0x00000204,0x00000000,0xb78fe6d8,0x0000001c,(nil)),stub!
fixme:psapi:EnumProcessModules (hProcess=0xffffffff, 0xb78fea64, 2048, 0xb78ff6b0): stub
fixme:ver:GetVersionExA OSVERSIONINFOA is too large (possibly OSVERSIONINFOEXA)
/usr/bin/cvscedega: line 87: 19878 Segmentation fault      "$ConfigurePrefix/bin/$WineExecName" "$@"

```

I really don't know where to start, since it doesn't look like any one error messed it up more than another.

I've heard setting less agressive CFLAGS then recompiling will help, but that really doesn't mean anything to me since I used a shell script to download/compile cvscedega in the first place.  any tips?

---

### Post by OneSeventeen on 2005-08-26
Anybody?? Anybody?

Bueller?



Oh, and one more question, I installed via the standard SteamInstall.exe from steampowered.com, not the SteamInstall_CS.exe that I heard about in the tutorial I followed.  (which also did not link to the SteamInstall_CS.exe file anywhere....)

Just a thought, anyone else here get Counter Strike: Source to work properly?

---

### Post by OneSeventeen on 2005-08-28
Well, I got SteamInstall_CS.exe and it didn't really do anything different that I can tell, other than it probably actually installed counter-strike.

Could it be because I'm using a linux filesystem instead of FAT?

I really want to get this working, so if you have any tips at all, plese let me know.

---

