---
title: "WoW Problems"
date: 2007-08-14
forum: Gaming &amp; Leisure
---

### Post by Lumbendil on 2007-08-14
I tryed to setup Wine in order to make WoW to run (as shown in the how to). It didnt work much well, it went at a terrible speed in the Login Screen and thus, when i logged a character, because of i belive major delay with getting reponse from my PC, i get kicked out of the server. I decided to try to install the nVidia drivers i can find with Ubuntu (7.04) app manager, and i now get the following errors:

```
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7d770000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d770000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
err:wgl:get_render_type_from_fbconfig Unknown render_type: 0
err:d3d:WineD3D_CreateFakeGLContext Can't find a suitable iPixelFormat
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreatePbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleasePbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyPbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryPbufferARB) - not found
err:d3d:IWineD3DImpl_FillGLCaps    GL_Extensions returns NULL
err:d3d:InitAdapters Failed to initialize gl caps for default adapter
err:wine_d3d:WineDirect3DCreate Direct3D9 is not available without opengl

```

Before adding the nVidia drivers, i got some errors aswell before running WoW, wich would be the following:
```
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7d750000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d750000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreatePbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleasePbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyPbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryPbufferARB) - not found
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f584,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wave:wodOpen fragment size set failed, size is now 1060
Your Open Sound System driver did not let us configure small enough sound fragments.
This may cause delays and other problems in audio playback with certain applications.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:reg:GetNativeSystemInfo (0x374026c4) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7cbe6494) stub!
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
*********************************WARN_ONCE*********************************
File r300_vertexprog.c function valid_dst line 333
Output 3 not used by fragment program
***************************************************************************
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 424
Software fallback:ctx->Multisample.Enabled
***************************************************************************
Try R300_SPAN_DISABLE_LOCKING env var if this hangs.
fixme:imm:ImmAssociateContextEx (0x30024, (nil), 16): stub

```

---

### Post by Lumbendil on 2007-08-15
I thought my graphic card was an nVidia but when i checked hardware it was an ATI...i've uninstalled nVidia package, installed ATI one, but now i'm getting the following problem after the edit of the config.wtf and the registry edit:
```
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7e080000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7e080000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f520,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x23), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x23), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x23!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f520,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x23), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x23!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f520,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x23), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x23!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f520,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x23), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x23!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f520,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x23), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x23!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f520,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x23), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x23!

```
Also, says:
World of Warcraft hasn't been able to start 3D acceleration

Tnx in advance for help ^^

EDIT: As for Launcher.exe, download freezes when there are 16 kbs downloaded

---

### Post by starcannon on 2007-08-19
Same exact errors here on intel X3100 integrated card on 1420n Ubuntu Edition laptop from Dell.

---

