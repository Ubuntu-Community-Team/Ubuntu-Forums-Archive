---
title: "WINE WoW Question"
date: 2006-11-15
forum: Gaming &amp; Leisure
---

### Post by Drezliok on 2006-11-15
I've installed it and got it to work. but I noticed my Terminal give me this:

```

drezliok@TuxEater:~$ wine ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/WoW.exe
fixme:midi:OSS_MidiInit Synthesizer supports MIDI in. Not yet supported.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7cbd0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cbd0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eeec,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f660,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f64c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33f168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wgl:X11DRV_wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:win:EnumDisplayDevicesW ((null),0,0x33e4f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e550,0x00000000), stub!
err:wgl:X11DRV_wglGetPixelFormatAttribivARB Unable to convert iPixelFormat 0 to a GLX one, expect problems!
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub

```

Is there anything in there I can fix?

```

err:wgl:X11DRV_wglGetPixelFormatAttribivARB Unable to convert iPixelFormat 0 to a GLX one, expect problems!

``` That one seems to make it get choppy once in a while but will clear up somewhat.

Very Playable, Very fun.

Thankyou, for your time and wisdom.
Drezliok

PS
How would I get it not to resize my desktop up to 1600x1200? I prefer 1280x960 72hz?

Thanks again.

---

### Post by hikaricore on 2006-11-15
run in terminal:

```
gedit /directoryofwow/wow
```

paste:

```

#~ /bin/bash
cd /driectoryofwow
WINEDEBUG=fixme-all,err-all,warn+cursor wine explorer /desktop=wow,1280x960 WoW.exe -opengl
```

save, exit, and:

```
chmod +x /directoryofwow/wow
```

Make a launcher and you should be set.  Modify the WINEDEBUG settings as needed. :)

This will only make a window of wow at the resolution you specified, but it basicly solves the issue :)

---

### Post by Drezliok on 2006-11-15
I got it to work but it was in a window. Not what I wanted.

Also, I am already using a laucher out of my usr/local/bin.

I've installed a new game into my Wine, same problem persists with it.

---

### Post by hikaricore on 2006-11-16
well atleast it fixes your errors, 1 problem solved.

---

