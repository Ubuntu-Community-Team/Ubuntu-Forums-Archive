---
title: "WoW Loads REALLY slowly but plays fine"
date: 2007-01-31
forum: Gaming &amp; Leisure
---

### Post by chadk on 2007-01-31
World of warcraft has been working fine but lately it's loading REALLY slow, like 5-8 minutes to load the login screen.  Anyone else?

wine .wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl &

---

### Post by Ferrat on 2007-01-31
> **chadk said:**
> World of warcraft has been working fine but lately it's loading REALLY slow, like 5-8 minutes to load the login screen.  Anyone else?

wine .wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe -opengl &

Nope, my loading speed is faster than in Windows and I load faster than most in instances ect. 

have you tried looking at what your terminal says during the loading??

---

### Post by chadk on 2007-01-31
```
chad@figment:~$ ./wow.sh
chad@figment:~$ fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7cfc0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cfc0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:win:EnumDisplayDevicesW ((null),0,0x33d058,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d0b0,0x00000000), stub!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:ntdll:RtlpWaitForCriticalSection section 0x88056cc "?" wait timed out in thread 0015, blocked by 0009, retrying (60 sec)
fixme:win:EnumDisplayDevicesW ((null),0,0x33d0b0,0x00000000), stub!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)

```
I'm still playing right now... this is the current output.

It takes 2-3 minutes for the first line
```
fixme:advapi:SetSecurityInfo stub
```
and 3-4 minutes for the next batch:
```
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7cfc0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cfc0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!

```

Then I get the login screen.

---

### Post by Sammi on 2007-02-01
Reinstall WoW and Wine? :D

---

### Post by hikaricore on 2007-02-01
Wow only takes like a minute or so to open here.

Zoning as others have mentioned is much faster than windows.

---

