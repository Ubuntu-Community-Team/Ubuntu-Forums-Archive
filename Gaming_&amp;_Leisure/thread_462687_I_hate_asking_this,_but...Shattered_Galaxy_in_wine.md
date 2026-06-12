---
title: "I hate asking this, but...Shattered Galaxy in wine?"
date: 2007-06-03
forum: Gaming &amp; Leisure
---

### Post by yosser on 2007-06-03
I tried installing it using just wine "Sgalaxy182.exe", it loads up, then I get this error:


```
fixme:ntdll:NtQuerySecurityObject (0x7c,0x00000007,0x521848,0x0000f000,0x33e71c) stub!
fixme:ntdll:NtQuerySecurityObject (0x7c,0x00000007,0x521848,0x0000f000,0x33e71c) stub!
fixme:shell:IShellLinkA_fnGetPath (0x1ba958): WIN32_FIND_DATA is not yet filled.
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:IShellLinkA_fnGetPath (0x17bf10): WIN32_FIND_DATA is not yet filled.
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink
fixme:shell:IShellLinkA_fnGetPath (0x17dd48): WIN32_FIND_DATA is not yet filled.
err:module:import_dll Library MSVBVM60.DLL (which is needed by L"C:\\Program Files\\KRU\\Shattered Galaxy\\thidchk.dll") not found

```

What can I do to fix this?

---

### Post by hikaricore on 2007-06-03
It may not make it work, but my guess would be to download MSVBVM60.DLL and place it in:

> ~/.wine/drive_c/windows/system32

---

