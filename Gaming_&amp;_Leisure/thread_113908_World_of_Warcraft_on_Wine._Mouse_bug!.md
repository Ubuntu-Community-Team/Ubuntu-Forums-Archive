---
title: "World of Warcraft on Wine. Mouse bug!"
date: 2006-01-07
forum: Gaming &amp; Leisure
---

### Post by Flaringo on 2006-01-07
Hi.

I am running Kubuntu and Wine 0.9.5.

Recently i tried World of Warcraft on wine, it went perfectly, but, I can't select anything :(

Then, I went on to google, forums etc. 
I figured out that i needed a patch, wich have to be applied to the Wine CVS souce-thingy. 

Is there any other way? I have NO idea about how to do it(apply the patch, install CVS). 
 
If there is no other way, can anyone please make/link a detailed guide about how?



Thanks,
Flaringo.

---

### Post by souled on 2006-01-07
Run this command in the terminal ```
 export WINEPRELOADER_SETVALEGACY="no"
```
Then run WoW from the same terminal. Not sure how the command works, but it fixes the problem for me.

---

### Post by Flaringo on 2006-01-07
Hmm. It didn't work. :(

EDIT: Now it doesn't work at all :( 

```
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c610000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c610000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0eef4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f160,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f700,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f700,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f668,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0f654,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0ee70,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:imm:ImmGetContext (0x10022): stub
fixme:opengl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0e50c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb0e564,0x00000000), stub!
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  418
  Current serial number in output stream: 419
```

---

