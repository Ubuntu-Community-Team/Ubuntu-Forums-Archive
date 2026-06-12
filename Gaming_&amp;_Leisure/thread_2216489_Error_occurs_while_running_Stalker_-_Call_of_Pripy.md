---
title: "Error occurs while running Stalker - Call of Pripyat using Wine 1.7.1.15"
date: 2014-04-12
forum: Gaming &amp; Leisure
---

### Post by ardous.anto on 2014-04-12
Hi all,

I am a complete newbie to linux and I am facing a steep learning curve at the moment.
I tried to install Stalker - Call of Pripyat game, installed wine 1.7.15 and ran the installer the installation was fine, but when i ran the command "wine ./bin/xrEngine.exe" from the terminal, the following is the error i got.

antony@AntonyPC:/media/GAMES/S.T.A.L.K.E.R. - Call of Pripyat$ wine ./bin/xrEngine.exe 
fixme:msvcrt:__clean_type_info_names_internal (0x1489278) stub
fixme:msvcrt:__clean_type_info_names_internal (0x14ba298) stub
fixme:msvcrt:__clean_type_info_names_internal (0x14c3018) stub
fixme:msvcrt:__clean_type_info_names_internal (0x10012ac8) stub
fixme:msvcrt:__clean_type_info_names_internal (0x26f978) stub
fixme:msvcrt:__clean_type_info_names_internal (0x1445a68) stub
antony@AntonyPC:/media/GAMES/S.T.A.L.K.E.R. - Call of Pripyat$ fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:actctx:parse_assembly_elem wrong namespace L"urn:schemas-microsoft-com:asm.v2"
fixme:actctx:parse_manifest_buffer failed to parse manifest (null)
fixme:exec:SHELL_execute flags ignored: 0x00000100
fixme:actctx:parse_assembly_elem wrong namespace L"urn:schemas-microsoft-com:asm.v2"
fixme:actctx:parse_manifest_buffer failed to parse manifest (null)
fixme:heap:HeapSetInformation 0x240000 0 0x23f6c0 4
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:win:EnumDisplayDevicesW ((null),0,0x1408f88,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1408b08,0x00000000), stub!
fixme:reg:RegDisableReflectionKey 0x140ab1c: stub
fixme:file:K32EnumPageFilesA (0x9518d0, 0x13e97e4) stub
fixme:file:K32EnumPageFilesA (0x9518d0, 0x13b4100) stub
fixme:win:EnumDisplayDevicesW ((null),0,0x1350308,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x134fe88,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x1350308,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x134fe88,0x00000000), stub!
fixme:reg:RegDisableReflectionKey 0x13dc508: stub
fixme:reg:RegDisableReflectionKey 0x13dc4f8: stub
fixme:reg:RegDisableReflectionKey 0x13dc4f4: stub
fixme:reg:RegDisableReflectionKey 0x13dc4f4: stub
fixme:reg:RegDisableReflectionKey 0x13dc4f4: stub
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQuerySystemInformation (0x00000007,0x13e1d08,0x00000018,(nil)) stub
fixme:reg:RegDisableReflectionKey 0x13e013c: stub
fixme:cdrom:CDROM_GetMediaType : faking success
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:server_ioctl_file Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:ntdll:server_ioctl_file Unsupported ioctl 4d0008 (device=4d access=0 func=2 method=0)
fixme:mountmgr:harddisk_ioctl Unsupported ioctl 2d1400 (device=2d access=0 func=500 method=0)
fixme:cursor:SetSystemCursor (0x20048,00007f00),stub!
fixme:cursor:SetSystemCursor (0x10070,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1007e,00007f03),stub!
fixme:cursor:SetSystemCursor (0x1008c,00007f01),stub!
fixme:cursor:SetSystemCursor (0x1009a,00007f88),stub!
fixme:cursor:SetSystemCursor (0x100a8,00007f86),stub!
fixme:cursor:SetSystemCursor (0x100b6,00007f83),stub!
fixme:cursor:SetSystemCursor (0x100c4,00007f82),stub!
fixme:cursor:SetSystemCursor (0x100d2,00007f84),stub!
fixme:cursor:SetSystemCursor (0x100e0,00007f04),stub!
fixme:cursor:SetSystemCursor (0x100ee,00007f02),stub!
fixme:cursor:SetSystemCursor (0x20048,00007f00),stub!
fixme:cursor:SetSystemCursor (0x9003e,00007f00),stub!
fixme:cursor:SetSystemCursor (0x7004c,00007f03),stub!
fixme:cursor:SetSystemCursor (0x1004e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x10052,00007f88),stub!
fixme:cursor:SetSystemCursor (0x10056,00007f86),stub!
fixme:cursor:SetSystemCursor (0x1005a,00007f83),stub!
fixme:cursor:SetSystemCursor (0x1005e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x10062,00007f82),stub!
fixme:cursor:SetSystemCursor (0x10066,00007f84),stub!
fixme:cursor:SetSystemCursor (0x1006a,00007f04),stub!
fixme:cursor:SetSystemCursor (0x1006e,00007f02),stub!
fixme:ntdll:NtQueryInformationProcess (process=0xffffffff) Unimplemented information class: ProcessDeviceMap
fixme:reg:RegDisableReflectionKey 0x141f86c: stub
fixme:ntdll:NtQuerySystemInformation info_class SYSTEM_HANDLE_INFORMATION
fixme:ntdll:NtQueryObject Unsupported information class 3
err:rpc:I_RpcGetBuffer no binding
fixme:msvcrt:MSVCRT__set_abort_behavior _WRITE_CALL_REPORTFAULT unhandled
fixme:heap:HeapSetInformation 0x110000 0 0x141f2a0 4
err:ole:CoInitializeEx Attempt to change threading model of this apartment from multi-threaded to apartment threaded
fixme:gameux:GameExplorer2Impl_CheckAccess stub (0x13d770, L"Z:\\media\\GAMES\\S.T.A.L.K.E.R. - Call of Pripyat\\Stalker-COP.exe", 0x141e848)
fixme:msvcrt:__clean_type_info_names_internal (0x1f43340) stub
fixme:msvcrt:MSVCRT__set_abort_behavior _WRITE_CALL_REPORTFAULT unhandled
fixme:thread:SetThreadIdealProcessor (0xfffffffe): stub
fixme:thread:SetThreadIdealProcessor (0x270): stub
fixme:thread:SetThreadIdealProcessor (0x274): stub
fixme:thread:SetThreadIdealProcessor (0x27c): stub
fixme:win:EnumDisplayDevicesW ((null),0,0x141eb18,0x00000000), stub!
fixme:msvcrt:__clean_type_info_names_internal (0x453d7e8) stub
fixme:msvcrt:__clean_type_info_names_internal (0x43841b0) stub
fixme:msvcrt:__clean_type_info_names_internal (0x435d018) stub
fixme:msvcrt:__clean_type_info_names_internal (0x2643478) stub
err:module:import_dll Loading library D3DCompiler_42.dll (which is needed by L"Z:\\media\\GAMES\\S.T.A.L.K.E.R. - Call of Pripyat\\bin\\xrRender_R3.dll") failed (error c000007b).
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXMatrixTranslation' used by L"C:\\windows\\system32\\d3dx10_43.dll"
err:module:find_forwarded_export function not found for forward 'd3dx10_43.D3DXMatrixTranslation' used by L"C:\\windows\\system32\\d3dx10_42.dll". If you are using builtin L"d3dx10_42.dll", try using the native one instead.
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXVec3TransformCoordArray' used by L"C:\\windows\\system32\\d3dx10_43.dll"
err:module:find_forwarded_export function not found for forward 'd3dx10_43.D3DXVec3TransformCoordArray' used by L"C:\\windows\\system32\\d3dx10_42.dll". If you are using builtin L"d3dx10_42.dll", try using the native one instead.
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXVec3Normalize' used by L"C:\\windows\\system32\\d3dx10_43.dll"
err:module:find_forwarded_export function not found for forward 'd3dx10_43.D3DXVec3Normalize' used by L"C:\\windows\\system32\\d3dx10_42.dll". If you are using builtin L"d3dx10_42.dll", try using the native one instead.
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXMatrixInverse' used by L"C:\\windows\\system32\\d3dx10_43.dll"
err:module:find_forwarded_export function not found for forward 'd3dx10_43.D3DXMatrixInverse' used by L"C:\\windows\\system32\\d3dx10_42.dll". If you are using builtin L"d3dx10_42.dll", try using the native one instead.
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXVec3TransformNormal' used by L"C:\\windows\\system32\\d3dx10_43.dll"
err:module:find_forwarded_export function not found for forward 'd3dx10_43.D3DXVec3TransformNormal' used by L"C:\\windows\\system32\\d3dx10_42.dll". If you are using builtin L"d3dx10_42.dll", try using the native one instead.
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXVec3Transform' used by L"C:\\windows\\system32\\d3dx10_43.dll"
err:module:find_forwarded_export function not found for forward 'd3dx10_43.D3DXVec3Transform' used by L"C:\\windows\\system32\\d3dx10_42.dll". If you are using builtin L"d3dx10_42.dll", try using the native one instead.
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXMatrixScaling' used by L"C:\\windows\\system32\\d3dx10_43.dll"
err:module:find_forwarded_export function not found for forward 'd3dx10_43.D3DXMatrixScaling' used by L"C:\\windows\\system32\\d3dx10_42.dll". If you are using builtin L"d3dx10_42.dll", try using the native one instead.
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXFloat32To16Array' used by L"C:\\windows\\system32\\d3dx10_43.dll"
err:module:find_forwarded_export function not found for forward 'd3dx10_43.D3DXFloat32To16Array' used by L"C:\\windows\\system32\\d3dx10_42.dll". If you are using builtin L"d3dx10_42.dll", try using the native one instead.
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXMatrixMultiply' used by L"C:\\windows\\system32\\d3dx10_43.dll"
err:module:find_forwarded_export function not found for forward 'd3dx10_43.D3DXMatrixMultiply' used by L"C:\\windows\\system32\\d3dx10_42.dll". If you are using builtin L"d3dx10_42.dll", try using the native one instead.
err:module:find_forwarded_export module not found for forward 'd3dx9_36.D3DXMatrixOrthoOffCenterLH' used by L"C:\\windows\\system32\\d3dx10_43.dll"
err:module:find_forwarded_export function not found for forward 'd3dx10_43.D3DXMatrixOrthoOffCenterLH' used by L"C:\\windows\\system32\\d3dx10_42.dll". If you are using builtin L"d3dx10_42.dll", try using the native one instead.
err:module:import_dll Loading library d3dx11_42.dll (which is needed by L"Z:\\media\\GAMES\\S.T.A.L.K.E.R. - Call of Pripyat\\bin\\xrRender_R4.dll") failed (error c000007b).
err:module:import_dll Loading library D3DCompiler_42.dll (which is needed by L"Z:\\media\\GAMES\\S.T.A.L.K.E.R. - Call of Pripyat\\bin\\xrRender_R4.dll") failed (error c000007b).
fixme:heap:RtlCompactHeap (0x110000, 0x0) stub
fixme:thread:start_thread Started native thread 00000027
fixme:thread:start_thread Started native thread 00000026
fixme:thread:start_thread Started native thread 00000025
fixme:thread:start_thread Started native thread 00000024
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x7d19f0bc

antony@AntonyPC:/media/GAMES/S.T.A.L.K.E.R. - Call of Pripyat$ 

============================================================

sorry about posting the entire log, i tried to add those dlls in wineconfig -> Add libraries but i still got the same error in the console. 
Thanks in advance.

---

