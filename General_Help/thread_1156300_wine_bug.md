---
title: "wine bug"
date: 2009-05-11
forum: General Help
---

### Post by bertolo on 2009-05-11
hi.
Since i upgraded to 9.04 i haven't been able to play cs 1.6 under my wine-1.1.21.

help plz
thks

---

### Post by Mirge on 2009-05-11
[http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true](http://appdb.winehq.org/objectManager.php?bIsQueue=false&bIsRejected=false&sClass=application&sTitle=Browse+Applications&iItemsPerPage=25&iPage=1&sOrderBy=appName&bAscending=true)

I don't see it in the supported apps database... what exactly is the problem you're experiencing? Crashes? Not loading? Explain please.

---

### Post by bertolo on 2009-05-11
when i join a server in the internet to start playing it crashes. and can't install new apps under wine too.

---

### Post by bertolo on 2009-05-11
the output when i try to run theme hospital setup

> 
WINEDEBUG=+loaddll wine Theme\ Hospital.exe 
trace:loaddll:load_builtin_dll Loaded L"KERNEL32.dll" at 0x7b820000: builtin
trace:loaddll:load_native_dll Loaded L"Z:\\home\\bertolo\\Downloads\\Theme Hospital\\Theme Hospital.exe" at 0x400000: native
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\advapi32.dll" at 0x7ee30000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\gdi32.dll" at 0x7eb80000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\user32.dll" at 0x7ec30000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\comctl32.dll" at 0x7ed60000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\shlwapi.dll" at 0x7e8e0000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\shell32.dll" at 0x7e940000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\winspool.drv" at 0x7e8a0000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\comdlg32.dll" at 0x7eac0000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\OLE32.DLL" at 0x65f00000: native
trace:loaddll:MODULE_LoadModule16 Loaded module "krnl386.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "system.drv" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "gdi.exe" : builtin
trace:loaddll:MODULE_LoadModule16 Loaded module "user.exe" : builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\imm32.dll" at 0x7e540000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\winex11.drv" at 0x7e6d0000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\uxtheme.dll" at 0x7e4e0000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\oleaut32.dll" at 0x65340000: native
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\riched20.dll" at 0x7e1e0000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\riched32.dll" at 0x7e480000: builtin
fixme:shell:SHAutoComplete SHAutoComplete stub
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\shdocvw.dll" at 0x7e190000: builtin
fixme:shdocvw:PersistStreamInit_InitNew (0x13b3a0)
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\mpr.dll" at 0x7e130000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\wininet.dll" at 0x7e080000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\urlmon.dll" at 0x7e150000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\mshtml.dll" at 0x7dfd0000: builtin
fixme:urlmon:URLMoniker_BindToObject use running object table
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\msvcrt.dll" at 0x7df60000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\winmm.dll" at 0x7ded0000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\ws2_32.dll" at 0x7de90000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\iphlpapi.dll" at 0x7de70000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\wsock32.dll" at 0x7e110000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\nspr4.dll" at 0x390000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\js3250.dll" at 0x1d60000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\plds4.dll" at 0x340000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\plc4.dll" at 0x3f0000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\nssutil3.dll" at 0x3d0000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\nss3.dll" at 0x1e30000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\smime3.dll" at 0x1f10000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\sqlite3.dll" at 0x1f40000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\ssl3.dll" at 0x1fc0000: native
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\msimg32.dll" at 0x7de60000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\usp10.dll" at 0x7de40000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\lz32.dll" at 0x7de20000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\version.dll" at 0x7de30000: builtin
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\xul.dll" at 0xb70000: native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\xpcom.dll" at 0x10000000: native
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\winealsa.drv" at 0x7dde0000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\msacm32.dll" at 0x7d440000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\msacm32.drv" at 0x7d470000: builtin
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\midimap.dll" at 0x7d430000: builtin
fixme:system:SetProcessDPIAware stub!
trace:loaddll:load_builtin_dll Loaded L"C:\\windows\\system32\\dwmapi.dll" at 0x7d420000: builtin
fixme:dwmapi:DwmIsCompositionEnabled 0x328644
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\freebl3.dll" at 0x2200000: native
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\freebl3.dll") - Symbol NSGetModule not found
trace:loaddll:free_modref Unloaded module L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\freebl3.dll" : native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\plugins\\npnul32.dll" at 0x2200000: native
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plugins\npnul32.dll") - Symbol NSGetModule not found
trace:loaddll:free_modref Unloaded module L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\plugins\\npnul32.dll" : native
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nss3.dll") - Symbol NSGetModule not found
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xpcom.dll") - Symbol NSGetModule not found
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\ssl3.dll") - Symbol NSGetModule not found
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\RPCRT4.DLL" at 0x70100000: native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\system32\\RPCRT4.DLL" : native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\RPCRT4.DLL" at 0x70100000: native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\system32\\RPCRT4.DLL" : native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\RPCRT4.DLL" at 0x70100000: native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\system32\\RPCRT4.DLL" : native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\nssdbm3.dll" at 0x2230000: native
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssdbm3.dll") - Symbol NSGetModule not found
trace:loaddll:free_modref Unloaded module L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\nssdbm3.dll" : native
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plds4.dll") - Symbol NSGetModule not found
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\sqlite3.dll") - Symbol NSGetModule not found
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\js3250.dll") - Symbol NSGetModule not found
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\plc4.dll") - Symbol NSGetModule not found
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\RPCRT4.DLL" at 0x70100000: native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\system32\\RPCRT4.DLL" : native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\RPCRT4.DLL" at 0x70100000: native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\system32\\RPCRT4.DLL" : native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\RPCRT4.DLL" at 0x70100000: native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\system32\\RPCRT4.DLL" : native
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssutil3.dll") - Symbol NSGetModule not found
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\nssckbi.dll" at 0x2260000: native
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nssckbi.dll") - Symbol NSGetModule not found
trace:loaddll:free_modref Unloaded module L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\nssckbi.dll" : native
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\xul.dll") - Symbol NSGetModule not found
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\smime3.dll") - Symbol NSGetModule not found
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\nspr4.dll") - Symbol NSGetModule not found
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\RPCRT4.DLL" at 0x70100000: native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\system32\\RPCRT4.DLL" : native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\RPCRT4.DLL" at 0x70100000: native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\system32\\RPCRT4.DLL" : native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\RPCRT4.DLL" at 0x70100000: native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\system32\\RPCRT4.DLL" : native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\RPCRT4.DLL" at 0x70100000: native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\system32\\RPCRT4.DLL" : native
trace:loaddll:load_native_dll Loaded L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\softokn3.dll" at 0x22a0000: native
0[14cc10]: nsNativeModuleLoader::LoadModule("C:\windows\gecko\0.9.1\wine_gecko\softokn3.dll") - Symbol NSGetModule not found
trace:loaddll:free_modref Unloaded module L"C:\\windows\\gecko\\0.9.1\\wine_gecko\\softokn3.dll" : native
fixme:iphlpapi:NotifyAddrChange (Handle 0xac9e888, overlapped 0xac9e890): stub
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\rpcrt4.dll" at 0x70100000: native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\system32\\rpcrt4.dll" : native
err:module:DelayLoadFailureHook failed to delay load rpcrt4.dll.NdrClientInitializeNew
wine: Call from 0x7b844453 to unimplemented function rpcrt4.dll.NdrClientInitializeNew, aborting
trace:loaddll:load_native_dll Loaded L"C:\\windows\\system32\\rpcrt4.dll" at 0x70100000: native
trace:loaddll:free_modref Unloaded module L"C:\\windows\\system32\\rpcrt4.dll" : native
err:module:DelayLoadFailureHook failed to delay load rpcrt4.dll.I_RpcExceptionFilter
wine: Call from 0x7b844453 to unimplemented function rpcrt4.dll.I_RpcExceptionFilter, aborting
wine: Unimplemented function rpcrt4.dll.I_RpcExceptionFilter called at address 0x7b844453 (thread 0013), starting debugger...


---

### Post by IamWayne on 2009-05-11
That's just it, I've never gotten a thing at all to work under WINE! It just doesn't work for me.

---

### Post by bertolo on 2009-05-11
noone ?

---

