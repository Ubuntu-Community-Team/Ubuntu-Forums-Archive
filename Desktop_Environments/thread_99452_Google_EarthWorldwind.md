---
title: "Google Earth/Worldwind"
date: 2005-12-05
forum: Desktop Environments
---

### Post by simplyw00x on 2005-12-05
Has anyone had any luck with either of these? I tried GE with wine and got the following:

```
fixme:actctx:CreateActCtxW stub!
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
fixme:wave:ALSA_ComputeCaps Device has a minimum of 2 channels
err:ole:CoGetClassObject class {4955dd33-b159-11d0-8fcf-00aa006bcc59} not registered
err:ole:CoGetClassObject no class object {4955dd33-b159-11d0-8fcf-00aa006bcc59} could be created for for context 0x1
fixme:ole:CoCreateInstance no classfactory created for CLSID {4955dd33-b159-11d0-8fcf-00aa006bcc59}, hres is 0x80040154
fixme:font:load_VDMX Failed to retrieve vTable
fixme:font:load_VDMX Failed to retrieve vTable
fixme:font:load_VDMX Failed to retrieve vTable
fixme:imm:ImmGetContext (0x10020): stub
fixme:imm:ImmReleaseContext (0x10020, 0x7fdde558): stub
```

Trying reccomended DLL overrides resulted in:
> err:module:import_dll Library base.dll (which is needed by L"C:\\Program Files\\Google\\Google Earth\\etfile.dll") not found
err:module:import_dll Library etfile.dll (which is needed by L"C:\\Program Files\\Google\\Google Earth\\support.dll") not found
err:module:import_dll Library ole32.dll (which is needed by L"C:\\Program Files\\Google\\Google Earth\\qt-mt335.dll") not found
err:module:import_dll Library qt-mt335.dll (which is needed by L"C:\\Program Files\\Google\\Google Earth\\base.dll") not found
Yet all of these DLL files are present. Lolwhat?

ww2d works fine except it segfaults after about 10 seconds.


Any ideas?

---

