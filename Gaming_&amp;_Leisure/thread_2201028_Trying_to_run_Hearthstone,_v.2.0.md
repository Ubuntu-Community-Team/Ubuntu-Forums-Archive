---
title: "Trying to run Hearthstone, v.2.0"
date: 2014-01-22
forum: Gaming &amp; Leisure
---

### Post by Ertai87 on 2014-01-22
I made a thread about trying to run Hearthstone on my pretty awful computer a while back, but I just on a whim tried again and the error message I got was significantly more helpful this time.  Upon running Hearthstone Beta Launcher.exe, I get stuck on the "Waiting for Updates" screen, and in console I get a cycling bunch of log text.  If any of that is helpful, let me know and I can post it for you.  For now, though, I tried running Hearthstone.exe, and here's what I got.

In the log:

```
~/.wine/drive_c/Program Files/Hearthstone$ wine Hearthstone.exe 
fixme:heap:HeapSetInformation (nil) 1 (nil) 0
Mono path[0] = 'C:/Program Files/Hearthstone/Hearthstone_Data/Managed'
Mono path[1] = 'C:/Program Files/Hearthstone/Hearthstone_Data/Mono'
Mono config path = 'C:/Program Files/Hearthstone/Hearthstone_Data/Mono/etc'
fixme:imm:ImmReleaseContext (0x10048, 0x144480): stub
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f778,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f578,0x00000000), stub!
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f458,0x00000000), stub!
fixme:dxgi:dxgi_output_GetDesc iface 0x14cd70, desc 0x33fa1c stub!
fixme:wbemprox:client_security_SetBlanket 0xb7310330, 0x14ce10, 10, 0, (null), 3, 3, (nil), 0x00000000
fixme:wbemprox:client_security_Release 0xb7310330
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8A8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:d3d:check_fbo_compat Format WINED3DFMT_B8G8R8X8_UNORM with rendertarget flag is not supported as FBO color attachment, and no fallback specified.
fixme:win:EnumDisplayDevicesW ((null),0,0x33f368,0x00000000), stub!
fixme:winediag:AUDDRV_GetAudioEndpoint Winepulse is not officially supported by the wine project
fixme:winediag:AUDDRV_GetAudioEndpoint For sound related feedback and support, please visit http://ubuntuforums.org/showthread.php?t=1960599
fixme:win:RegisterRawInputDevices Unhandled flags 0x100 for device 0.
fixme:win:RegisterDeviceNotificationW (hwnd=0x10048, filter=0x33fc6c,flags=0x00000000) returns a fake device notification handle!
err:wgl:glxdrv_wglShareLists Could not share display lists, one of the contexts has been current already !
err:wgl:glxdrv_wglShareLists Could not share display lists, one of the contexts has been current already !

```

On my virtual desktop screen: [ATTACH=CONFIG]249658[/ATTACH]

Help appreciated!

---

### Post by leo-ms on 2014-01-22
Did you try launching it within a virtual desktop environment on Wine?

---

### Post by Ertai87 on 2014-01-22
> **leo-ms said:**
> Did you try launching it within a virtual desktop environment on Wine?

I did indeed.  Hence the line beside the picture: "On my virtual desktop screen"

---

