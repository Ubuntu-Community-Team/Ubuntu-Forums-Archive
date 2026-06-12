---
title: "been playing wow. tried switching to a better videocard. now it wont work."
date: 2007-02-13
forum: Gaming &amp; Leisure
---

### Post by graigsmith on 2007-02-13
so, i had been happily playing WOW. on my 9200 radeon with very low frame rates.  using open source drivers.

so i swiched cards out. to try my radeon x800.  I read that the open source 3d driver for the x800 has 3d support.   i have 3d running on it.  glxinfo reports direct rendering is true.   but when i launch the game, it freezes. barely gets to the graphics.  and when it does get to the graphics it doesn't do much.     direct 3d mode wont work either. 

anyone have any thoughts as to how to fix this?

---

### Post by graigsmith on 2007-02-13
when i run wow from the command line, this is the printout text.

```
graig@graig-desktop:~/.wine/drive_c/Program Files/World of Warcraft$ wine wow.exe
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
err:secur32:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.24 is in your path.
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7d560000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d560000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1792c0) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1792c0) Unhandled query type 9
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1792c0) Unhandled query type 8
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:d3d:state_psizemin WINED3DRS_POINTSIZE_MIN not supported on this opengl, value is 0.000000
fixme:d3d:state_psizemax WINED3DRS_POINTSIZE_MAX not supported on this opengl, value is 1.000000
*********************************WARN_ONCE*********************************
File r300_vertexprog.c function t_dst_index line 184
Unknown output 3
***************************************************************************
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 406
Software fallback:ctx->Multisample.Enabled
***************************************************************************
Try R300_SPAN_DISABLE_LOCKING env var if this hangs.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
Killed

```

---

### Post by Sammi on 2007-02-13
A lot of ATI related crashes have been reported and fixed on this page: [http://appdb.winehq.org/appview.php?iVersionId=6482](http://appdb.winehq.org/appview.php?iVersionId=6482)

Try to search for your problem in the many posts found there.

---

