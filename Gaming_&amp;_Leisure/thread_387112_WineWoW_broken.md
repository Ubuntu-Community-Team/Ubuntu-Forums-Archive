---
title: "Wine/WoW broken?"
date: 2007-03-17
forum: Gaming &amp; Leisure
---

### Post by noenter1 on 2007-03-17
Ok I am very confused on this one and need some help. I got a new graphics card the other day and i installed the driver using envy. ([http://albertomilone.com/projects.html](http://albertomilone.com/projects.html)) I first did this on my test ubuntu boot(both are 6.10 same machine). It worked, then I tried it on my other ubuntu boot, but this time it didn't work and for some reason I couldn't get it to work(even tried reverting back to the previous driver). I thought ok no problem ill just install wine on my other boot. Ventrillo worked fine WoW installed, but it wont run.(aoss wine 'C:/Program Files/World of Warcraft/WoW.exe' -opengl) so i typed this into the terminal and got:
```
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/$LIB/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7e2b0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7e2b0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  28 ()
  Serial number of failed request:  505
  Current serial number in output stream:  506
```
Can someone help with this please?
Thanks in advance for any and all help.

---

### Post by hikaricore on 2007-03-17
For most people (myself included) WoW works fine with wine.

What version of wine are you using?  Are you _sure_ your video drivers are installed 
properly?

```
glxinfo | grep rendering
```

The community wiki for WoW is found here if you need any ideas where to start: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

---

### Post by noenter1 on 2007-03-17
Using Wine 0.9.32
```
glxinfo | grep rendering
direct rendering: Yes
```
All the dll files were already installed(i followed the wiki for instalation)
I noticed when i tried it again the screen flashes for a quik second. Also tried opening it in d3d mod, it worked but was very choppy.
Also im using a geforece 8800gtx.

---

### Post by hikaricore on 2007-03-18
Hmm... I'm not really sure at this point.  You may want to check that your X session is set to 24 bit colour.  

I've had some issues attempting to run opengl in 16bit for some reason on certain cards.

My only other suggestion would be trying windowed mode as well as logging into the game in d3d mode and turning off glow effects and other misc video options/setting options to low, logging out then starting again in opengl mode to test the changes.  Sometimes one little video option kills the whole game.

Hopefully you'll stumble onto something. >.<

---

### Post by noenter1 on 2007-03-18
Well good news and bad news... Apperrently i had typed in a command wrong when i installed my driver. So both ubuntu boots work now. Now the bad news, the sound seems to be broken. And wow still works in the other boot(will investigate the differences).

---

