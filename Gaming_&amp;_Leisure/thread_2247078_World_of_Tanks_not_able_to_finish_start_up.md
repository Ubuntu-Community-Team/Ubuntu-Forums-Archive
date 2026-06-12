---
title: "World of Tanks not able to finish start up"
date: 2014-10-05
forum: Gaming &amp; Leisure
---

### Post by Dragonbite on 2014-10-05
I've been trying to run World of Tanks on my Ubuntu 12.04 system through PlayOnLinux for a while now (so I can either get rid of the version on the Windows computer, or be able to platoon with my son).  When I run it, it gets to the login screen and updating my garage.. and then closes.

I'm not sure if it is something with the graphics drivers, a wine component not being used in PlayOnLinux or the video card just cannot handle it.  It is one of those small form factor Optiplex so if I need to replace the video card I need to make sure it runs in a short slot (but if anybody has a recommendation that is < $100 and is Linux compatible, I am interested in finding out).

I know my system is a bit weak for gaming, but it is more powerful than the system I currently play on (I think).  It is a Dell Optiplex 745 with an Intel Core 2 Duo and 6 GB of RAM running Ubuntu 12.04 64bit.
```
$ lspci
00:00.0 Host bridge: Intel Corporation 82Q963/Q965 Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82Q963/Q965 PCI Express Root Port (rev 02)
00:1a.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HB/HR (ICH8/R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801H (ICH8 Family) 4 port SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801HR/HO/HH (ICH8R/DO/DH) 2 port SATA Controller [IDE mode] (rev 02)
[B]01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV516 [Radeon X1300/X1550 Series]
01:00.1 Display controller: Advanced Micro Devices, Inc. [AMD/ATI] RV516 [Radeon X1300/X1550 Series] (Secondary)
[/B]03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5754 Gigabit Ethernet PCI Express (rev 02)

```

The PlayOnLinux log file shows ```
mprox:client_security_Release 0xf43ff258
fixme:win:EnumDisplayDevicesW ((null),0,0x33d298,0x00000000), stub!
fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1dd8f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_HAL, src_format WINED3DFMT_B8G8R8A8_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
fixme:d3d:swapchain_init The application requested more than one back buffer, this is not properly supported.
Please configure the application to use double buffering (1 back buffer) if possible.
fixme:d3d:wined3d_swapchain_set_gamma_ramp Ignoring flags 0x1.
fixme:win:EnumDisplayDevicesW ((null),0,0x33d768,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d568,0x00000000), stub!
fixme:dxgi:dxgi_output_GetDesc iface 0x21fe40, desc 0x33db04 stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:client_security_SetBlanket 0xf43ff258, 0x21f618, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xf43ff258
fixme:win:EnumDisplayDevicesW ((null),0,0x33d468,0x00000000), stub!
fixme:d3d9:d3d9_device_CheckDeviceState iface 0x1fab80, dst_window 0x40088 stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:avrt:AvSetMmThreadCharacteristicsW (L"Audio",0x7a9e9a8): stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:win:EnumDisplayDevicesW ((null),0,0x33d7b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33b6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",0,0x33b3b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW (L"\\\\.\\DISPLAY1",1,0x33b3b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),1,0x33b6f8,0x00000000), stub!
fixme:d3d:state_zenable Z buffer disabled, but ARB_depth_clamp isn't supported.
**err:winediag:shader_generate_glsl_declarations The hardware does not support enough uniform components to run this shader, it may not render correctly.**
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:win:EnumDisplayDevicesW ((null),0,0x33e298,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e098,0x00000000), stub!
fixme:dxgi:dxgi_output_GetDesc iface 0xbccd1a0, desc 0x33e634 stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:client_security_SetBlanket 0xf43ff258, 0xbccdda8, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xf43ff258
fixme:win:EnumDisplayDevicesW ((null),0,0x33df98,0x00000000), stub!
fixme:imm:ImmReleaseContext (0x40088, 0x1ec4a638): stub
fixme:imm:NotifyIME NI_CLOSECANDIDATE
fixme:wbemprox:client_security_SetBlanket 0xf43ff258, 0x1ebae5d0, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xf43ff258
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:win:EnumDisplayDevicesW ((null),0,0x33e3d8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e1d8,0x00000000), stub!
fixme:dxgi:dxgi_output_GetDesc iface 0x1eb917c8, desc 0x33e770 stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
fixme:wbemprox:client_security_SetBlanket 0xf43ff258, 0x1433f7e8, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xf43ff258
fixme:win:EnumDisplayDevicesW ((null),0,0x33e0c8,0x00000000), stub!
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:wbemprox:wbem_services_CreateInstanceEnum unsupported flags 0x00000030
fixme:win:EnumDisplayDevicesW ((null),0,0x33ddb8,0x00000000), stub!
fixme:d3d9:Direct3DShaderValidatorCreate9 stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:wined3d_check_device_format_conversion wined3d 0x1dd8f0, adapter_idx 0, device_type WINED3D_DEVICE_TYPE_HAL, src_format WINED3DFMT_B8G8R8A8_UNORM, dst_format WINED3DFMT_B8G8R8X8_UNORM stub!
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:explorerframe:taskbar_list_SetProgressValue iface 0x12f858c0, hwnd 0x40088, ullCompleted 0, ullTotal 0 stub!
fixme:explorerframe:taskbar_list_SetProgressState iface 0x12f858c0, hwnd 0x40088, flags 0 stub!
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
radeon: The kernel rejected CS, see dmesg for more information.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:win:RegisterDeviceNotificationA (hwnd=0x9004c, filter=0x168fe970,flags=0x00000000) returns a fake device notification handle!
err:winsock:interface_bind Failed to bind to interface, receiving broadcast packets will not work on socket 053c.
err:winsock:interface_bind Failed to bind to interface, receiving broadcast packets will not work on socket 053c.
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33424c 63 English_US) semi-stub
fixme:msvcp:locale__Locimp__Makexloc (0x33424c 63 0x202cee00 (nil)) semi-stub
fixme:msvcp:locale__Locimp__Makewloc (0x33424c 63 0x202cee00 (nil)) semi-stub
fixme:msvcp:locale__Locimp__Makeushloc (0x33424c 63 0x202cee00 (nil)) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33424c 63 German_Germany) semi-stub
fixme:msvcp:locale__Locimp__Makexloc (0x33424c 63 0x202c20b8 (nil)) semi-stub
fixme:msvcp:locale__Locimp__Makewloc (0x33424c 63 0x202c20b8 (nil)) semi-stub
fixme:msvcp:locale__Locimp__Makeushloc (0x33424c 63 0x202c20b8 (nil)) semi-stub
fixme:msvcp:_Locinfo__Locinfo_ctor_cat_cstr (0x33424c 63 Russian_Russia) semi-stub
fixme:msvcp:locale__Locimp__Makexloc (0x33424c 63 0x202d0d60 (nil)) semi-stub
fixme:msvcp:locale__Locimp__Makewloc (0x33424c 63 0x202d0d60 (nil)) semi-stub
fixme:msvcp:locale__Locimp__Makeushloc (0x33424c 63 0x202d0d60 (nil)) semi-stub
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
fixme:d3d:resource_check_usage Unhandled usage flags 0x8.
err:ntdll:RtlpWaitForCriticalSection section 0x7d997698 "wined3d_main.c: wined3d_cs" wait timed out in thread 0018, blocked by 0027, retrying (60 sec)
```

and dmesg shows ```
[   29.662205] composite sync not supported
[   30.464142] composite sync not supported
[   55.099910] composite sync not supported
[  146.101471] composite sync not supported
[  146.352898] composite sync not supported
[  146.558117] composite sync not supported
[  916.192911] composite sync not supported
[  916.409221] composite sync not supported
[  917.061377] composite sync not supported
[  917.338545] composite sync not supported
[  921.387133] composite sync not supported
[  921.745759] composite sync not supported
[  942.367350] composite sync not supported
[  967.646961] composite sync not supported
[  967.893738] composite sync not supported
[  968.098849] composite sync not supported
[ 2104.092690] composite sync not supported
[ 2109.934908] composite sync not supported
[ 2110.134952] composite sync not supported
[ 2110.638173] composite sync not supported
[ 2110.920269] composite sync not supported
[ 3131.327379] composite sync not supported
[ 3132.360864] composite sync not supported
[ 3132.673291] composite sync not supported
[ 3152.982657] composite sync not supported
[ 4934.757283] composite sync not supported
[ 4934.957137] composite sync not supported
[ 4935.647053] composite sync not supported
[ 4936.007552] composite sync not supported
[ 5002.783792] composite sync not supported
[ 5003.331103] composite sync not supported
[ 5003.997855] composite sync not supported
[ 5023.410013] composite sync not supported
[ 5194.617534] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 214865 dwords have 1024 dwords
[ 5194.617540] [drm:r100_cs_track_check] *ERROR* Max indices 214865
[ 5194.617543] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.402909] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.402916] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.402920] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.428664] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.428670] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.428674] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.458265] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.458271] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.458275] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.466611] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.466617] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.466621] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.474705] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.474711] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.474714] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.505552] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.505558] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.505562] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.537353] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.537358] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.537360] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.543354] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.543359] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.543362] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.593291] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.593298] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.593301] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.619975] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.619981] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.619985] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.669894] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.669900] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.669904] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.695236] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.695242] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.695245] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.743978] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.743985] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.743988] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.770179] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.770185] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.770189] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.820900] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.820906] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.820910] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.894064] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.894070] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.894073] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.922118] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.922124] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.922128] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5205.990203] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5205.990209] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5205.990213] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.042027] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.042032] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.042035] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.071783] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.071789] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.071792] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.138166] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.138172] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.138176] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.147582] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.147589] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.147592] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.194426] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.194432] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.194436] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.219656] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.219662] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.219666] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.272426] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.272432] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.272436] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.339300] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.339306] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.339310] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.389378] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.389384] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.389388] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.438573] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.438579] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.438583] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.447083] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.447089] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.447092] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.495315] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.495321] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.495325] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.519962] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.519968] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.519971] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.575621] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.575627] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.575631] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.640082] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.640088] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.640092] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.647456] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.647463] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.647466] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.695678] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.695684] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.695688] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.720820] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.720826] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.720830] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.773501] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.773508] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.773511] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5206.797744] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5206.797751] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5206.797754] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.652744] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.652750] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.652754] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.678816] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.678822] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.678826] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.702690] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.702696] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.702699] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.710335] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.710341] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.710345] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.736220] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.736226] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.736230] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.744343] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.744350] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.744353] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.769901] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.769908] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.769911] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.776684] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.776690] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.776693] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.803010] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.803016] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.803019] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.810274] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.810281] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.810284] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.836403] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.836409] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.836412] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.844367] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.844373] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.844377] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.870357] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.870363] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.870367] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.877593] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.877599] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.877603] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.919282] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.919287] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.919289] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
[ 5221.924975] radeon 0000:01:00.0: (PW 1) Vertex array 2 need 218179 dwords have 1024 dwords
[ 5221.924980] [drm:r100_cs_track_check] *ERROR* Max indices 218179
[ 5221.924983] [drm:radeon_cs_ioctl] *ERROR* Invalid command stream !
```

Any advice/direction would be appreciated.  Thank you.

---

### Post by mastablasta on 2014-10-06
Have you checked this: [https://appdb.winehq.org/objectManager.php?sClass=version&iId=30767](https://appdb.winehq.org/objectManager.php?sClass=version&iId=30767)

what version is the game at? 

the porblme with these online games is they often have updates and "upgrades" and then they break any little compatibility they might have had.

also do you have proprietary drivers installed?

---

### Post by Dragonbite on 2014-10-06
I believe I am running the Open Source drivers.  I just look at the AMD's website and came up with a possible driver (ATI Catalyst&#8482; 9.3 Proprietary Linux x86 Display Driver) which I will try and see if it makes a difference.  I tried the proprietary driver years ago and it cause a number of issues but I'll try this one and see how it goes.

The latest version is 9.3.  For a while I could not get WoT to work even in Windows with I think version 9.0 but they fixed it since.

Is there anything that may be a benefit in 14.04 that could be missing from 12.04?

---

### Post by mastablasta on 2014-10-07
don't just install the fglrx drivers at random. if you look closely they support the card but not the current xorg or xserver. so installing old drivers on new system will break it.

And your card is no longer supported by AMD.

the only solution would be to use a lot older OS.

still I doubt it's the drivers. could be though. but since this chip is supposedly fully supported by opensource...

---

### Post by Dragonbite on 2014-10-07
I've been getting myself confused about updating the video drivers (how? which? what o do if it borks the system?) 

On this page, it the video card is in the 
> Fully Supported
All these Radeon(HD) cards and derivatives have good 3D acceleration support. This is not an exhaustive list:
[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

Then I found commands for installing here, but not sure which exactly should be installed : [https://help.ubuntu.com/community/BinaryDriverHowto/AMD]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD")

The AMD page includes a .run download, but I haven't a clue what to do with it or even how to run it : [http://support.amd.com/en-us/download/desktop/legacy?product=Legacy1&os=Linux%20x86_64]("http://support.amd.com/en-us/download/desktop/legacy?product=Legacy1&os=Linux%20x86_64")

So even if I wanted to update the drivers or install the proprietary drivers... I am not sure how to do that or what to install.  And the *Additional Drivers* application doesn't find anything.

So if the video card is no longer supported, should I look at replacing it with a more up-to-date one?  If so, as you can see I have enough trouble understanding how and what to install so I'm not sure how to determine which card would work the best for me.

---

### Post by mastablasta on 2014-10-07
an easy check if you can do that or not is to open additional drivers and see if you can install anything. if you can then you can do it through that app, if not then forget about it. you can only check if you have 3D acceleration or not. 

your chip likely does not have fglrx available as everything below Radeon HD 4000 series (or was it 3000!?! ) was dropped in 14.04.eh dropped is such a strong word - support was moved into opensource driver.

what you could do is update opensource driver this is done via xorg edgers PPA. not sure if it would solve the issue though.

---

### Post by Dragonbite on 2014-12-02
Ok, different computer, different version of World of Tanks and still not able to finish the game starting up.

I am using a laptop that is dual-boot with Windows, which is able to run World of Tanks (WoT).

Computer system:
 ```
drew@Unicorn:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

The graphics are not great, but are adequate.

I installed World of Tanks by downloading the installation program from the website, and running it in PlayOnLinux.  When I tried using the built-in script it gets done way too fast (it's ~ 8GB download) and running it sends me to the WoT website and not actually run the game.  So the version is the latest version (9.4?).  This version has been working after the fiasco with I think it was 8.9 or 9.0.

The game starts up and allows me to log in.  It gets to "updating my garage" before it just hangs.  Below is the log file for the running.  I cleared out the log file before trying to run it so that it only has what is captured during a single attempt  The log file is attached as a .zip file.

I am not sure if I need to add some Wine component and/or which one(s).

---

