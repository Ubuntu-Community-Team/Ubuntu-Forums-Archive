---
title: "Guitar Hero 3 won't start with Wine"
date: 2008-12-08
forum: General Help
---

### Post by boaty on 2008-12-08
This is the error I'm getting:

```
zach@zach-laptop:/media/Vista3/Program Files/Aspyr/Guitar Hero III$ wine GH3.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
Trying to load PE image for unsupported architecture (AMD-64)
err:module:import_dll Loading library OneX.DLL (which is needed by L"C:\\windows\\system32\\Wlanapi.dll") failed (error c000007b).
Trying to load PE image for unsupported architecture (AMD-64)
err:module:import_dll Loading library bcrypt.dll (which is needed by L"C:\\windows\\system32\\Wlanapi.dll") failed (error c000007b).
err:module:import_dll Library eappcfg.dll (which is needed by L"C:\\windows\\system32\\Wlanapi.dll") not found
err:module:import_dll Library Wlanapi.dll (which is needed by L"Z:\\media\\Vista3\\Program Files\\Aspyr\\Guitar Hero III\\IntelLaptopGaming.dll") not found
err:module:import_dll Library IntelLaptopGaming.dll (which is needed by L"Z:\\media\\Vista3\\Program Files\\Aspyr\\Guitar Hero III\\GH3.exe") not found
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT"
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\Vista3\\Program Files\\Aspyr\\Guitar Hero III\\GH3.exe" failed, status c0000135

```

Any help would be appreciated.

---

### Post by HotShotDJ on 2008-12-08
> **boaty said:**
> Any help would be appreciated.I'm not familiar with Guitar Hero 3, but I did find some information at WineHQ.  I don't know how helpful it is, but at least it might give you some ideas on how to proceed.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=9860](http://appdb.winehq.org/objectManager.php?sClass=version&iId=9860)

---

