---
title: "can't run nullDC in Xubuntu Karmic"
date: 2009-12-13
forum: Gaming &amp; Leisure
---

### Post by xjgnsdof on 2009-12-13
I'm running Wine 1.1.34 in Xubuntu 9.10 (32-bit). I'm trying to run nullDC, as I've seen many people do, but I get the following error message in Terminal:

```
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.VC80.CRT" (8.0.50608.0)
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\emones\\Downloads\\nullDC\\MSVCP80.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\emones\\Downloads\\nullDC\\emitter_Win32.dll") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\emones\\Downloads\\nullDC\\emitter_Win32.dll") not found
err:module:import_dll Library emitter_Win32.dll (which is needed by L"Z:\\home\\emones\\Downloads\\nullDC\\nullDC_1.0.3_mmu.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\emones\\Downloads\\nullDC\\MSVCP80.dll") not found
err:module:import_dll Library MSVCP80.dll (which is needed by L"Z:\\home\\emones\\Downloads\\nullDC\\nullDC_1.0.3_mmu.exe") not found
err:module:import_dll Library MSVCR80.dll (which is needed by L"Z:\\home\\emones\\Downloads\\nullDC\\nullDC_1.0.3_mmu.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\emones\\Downloads\\nullDC\\nullDC_1.0.3_mmu.exe" failed, status c0000135
```

Any ideas?

---

