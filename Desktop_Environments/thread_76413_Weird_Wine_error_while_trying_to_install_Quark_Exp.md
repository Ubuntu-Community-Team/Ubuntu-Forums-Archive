---
title: "Weird Wine error while trying to install Quark Express"
date: 2005-10-15
forum: Desktop Environments
---

### Post by the__collector on 2005-10-15
I'm having a weird problem with Wine when I try to install Quark Express 6.1.

The installation just halts and I have the following in my terminal:

```

$ sudo wine Desktop/Quark/setup.exe
fixme:msi:MsiInstallProductW L"C:\\windows\\temp\\_is60b\\isscript.msi" L"REBOOT=ReallySuppress ADDLOCAL=All"
fixme:msi:ACTION_HandleStandardAction UNHANDLED Standard Action L"SelfUnregModules"
fixme:msi:ACTION_HandleStandardAction UNHANDLED Standard Action L"RemoveFiles"
fixme:msi:ACTION_HandleStandardAction UNHANDLED Standard Action L"MoveFiles"
fixme:msi:ACTION_InstallFiles Write DiskPrompt
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:msi:ACTION_HandleStandardAction UNHANDLED Standard Action L"RemoveRegistryValues"
fixme:msi:ACTION_HandleStandardAction UNHANDLED Standard Action L"RemoveFolders"fixme:msi:MsiInstallProductW L"Z:\\home\\luc\\Desktop\\Quark\\QuarkXPress 6.1.msi" (null)
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7de127b8,0x7de127bc), stub!
fixme:ole:RpcChannelBuffer_GetDestCtx (0x7de127b4,0x7de127b8), stub!
err:msi:ITERATE_Actions Execution halted due to error (1603)

```

Does anybody know what to do?

---

