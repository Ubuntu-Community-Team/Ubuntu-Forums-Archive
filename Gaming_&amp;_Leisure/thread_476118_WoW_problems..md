---
title: "WoW problems."
date: 2007-06-16
forum: Gaming &amp; Leisure
---

### Post by chaosmachine06 on 2007-06-16
Well I installed and played WoW without my graphics card driver installed, wich it worked, but gave me 2 frames per second. So I installed my driver, everything apears to be working alright, 3d acceleration in glxinfo says its on, but now WoW wont start. when I try to start it in consol I get 

```
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7de50000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7de50000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
 Files/World of Warcraft/WoW.exe: main/renderbuffer.c:2041: _mesa_add_renderbuffer: Assertion `bufferName == BUFFER_DEPTH || bufferName == BUFFER_STENCIL || fb->Attachment[bufferName].Renderbuffer == ((void *)0)' failed.

```

Also, glxgears is running very slow. 40ish per second, where as before it was about 400.

---

### Post by hikaricore on 2007-06-17
Keep in mind that glxgears is not a proper benchmark.

But moving on...400fps is terrible and 40fps is post mortum.

Though I believe you that you're geting a *"Direct rendering : Yes"* response from **glxinfo** this may be
a hardware/driver issue.  Exactly what video hardware are you using and how did you install the driver?

---

### Post by chaosmachine06 on 2007-06-17
Well, I have a unichrome onboard card. I installed it strictly following this tutorial: [https://help.ubuntu.com/community/OpenChrome?highlight=%28openchrome%29](https://help.ubuntu.com/community/OpenChrome?highlight=%28openchrome%29) but now I dont find anything that tells me I have the video card installed. glxinfo now returns this:

X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17

---

