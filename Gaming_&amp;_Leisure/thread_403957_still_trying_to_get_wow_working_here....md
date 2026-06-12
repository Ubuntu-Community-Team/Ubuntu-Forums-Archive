---
title: "still trying to get wow working here..."
date: 2007-04-07
forum: Gaming &amp; Leisure
---

### Post by storky on 2007-04-07
i have been trying a long time to get wow working on my HP dv2000, but still with little luck. As soon as im past the two opening videos it crashes every time. I am using wine withe the opengl command added on. here is what is posted in the terminal before wow tries to boot

libGL warning: 3D driver claims to not support visual 0x5b
libGL warning: 3D driver claims to not support visual 0x5b
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c640000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c640000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f328,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f554,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f540,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0

---

### Post by Drezliok on 2007-04-07
[http://ubuntuforums.org/showthread.php?t=312482](http://ubuntuforums.org/showthread.php?t=312482)

And if your using ATI tough luck I guess.

---

### Post by storky on 2007-04-07
it says theres a way of helping things out for ati users at the bottom by editing the registy, i have no idea what ati is or if im using it but i did add the key.

---

### Post by hikaricore on 2007-04-07
> **storky said:**
> it says theres a way of helping things out for ati users at the bottom by editing the registy, i have no idea what ati is or if im using it but i did add the key.

You never told us what kind of video card you have.

> libGL warning: 3D driver claims to not support visual 0x5b

Is usually caused by either Intel or ATI drivers that aren't working quite right.

What kind of video card do you have in your computer?

ATI can be tricky to setup, and the linux Intel drivers are crap mostly due to Intel stopping their work on them a long time ago.

---

### Post by storky on 2007-04-07
i have an intel.....damn....is it at least open source so that others can create drivers for it or am i pretty much gonna hve to get a different card

---

### Post by hikaricore on 2007-04-08
The source for the drivers does exist and has been worked on, but it's still mostly so-so.

It's ok (depending on your system) for native linux games (16bit colour for best results), I used my intel integrated graphics for awhile,
but when I really got bored and wanted to play wow again, I got a nice Nvidia card for about 60$.  :)

---

