---
title: "[SOLVED] WOW stopped working in wine"
date: 2007-08-03
forum: Gaming &amp; Leisure
---

### Post by Chaoticwhizz on 2007-08-03
WOW has worked fine for days now. Yesterday, I downloaded updates to Kubuntu and now WOW wont even load. Error mesage I get from console are:

```
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:mixer:ALSA_MixerInit No master control found, disabling mixer
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7df00000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7df00000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f520,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f008,0x00000000), stub!
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  28 ()
  Serial number of failed request:  575
  Current serial number in output stream:  576

```
Also I believe this is related to the recent libx updates.

UPDATE: reinstalling my video driver fixed the issue.

---

### Post by xb9 on 2007-08-03
i have come across the same problem now, any luck fixing?

---

### Post by splintercellguy on 2007-08-03
Updates, like kernel updates? Probably you need to rectify your graphics driver. What card are you using?

---

### Post by xb9 on 2007-08-03
im using a nvidia 7400go

---

### Post by splintercellguy on 2007-08-03
The question was intended for the OP. Could you create a separate and new thread with your question restated in detail, and also have you installed kernel updates? If you do have the same exact issue as the OP, try Envy. [http://appdb.winehq.org/appview.php?iAppId=72](http://appdb.winehq.org/appview.php?iAppId=72)

---

### Post by xb9 on 2007-08-03
sorry, but hey i jus tfixed it, just reinstall your graphical drivers, worked for me :)

---

### Post by splintercellguy on 2007-08-03
No problem. The caveat with the video drivers is that you have to reinstall each time you update the kernel.

---

### Post by Chaoticwhizz on 2007-08-04
> **splintercellguy said:**
> Updates, like kernel updates? Probably you need to rectify your graphics driver. What card are you using?

Geforce 6200. I didnt download any kernal updates. They were libx updates and a couple of others. But yeah, reinstalling my Nvidia driver solved the problem. Thanks.

---

