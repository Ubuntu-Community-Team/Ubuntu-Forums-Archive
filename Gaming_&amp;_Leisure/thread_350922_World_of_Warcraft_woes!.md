---
title: "World of Warcraft woes!"
date: 2007-02-01
forum: Gaming &amp; Leisure
---

### Post by Deeper on 2007-02-01
Hi folks,

I'm having some problems, I'm trying to run World of warcraft with WINE, but when I do, I:
 a) have no sound
b) Can't use my mouse to interact with people (though I see the mouse icon and can move it, just cant click and interact). I can target enemies etc using the keyboard, but cant target with the mouse. 


When i run WoW with wine this is what i get in the console:

[PHP]
jay@ubuntu:~/wow$ wine wow.exe -opengl
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f5dc,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:opengl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9d058,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9d0b0,0x00000000), stub!
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  13 (X_GLXCreateGLXPixmap)
  Serial number of failed request:  448
  Current serial number in output stream:  449
jamie@ubuntu-wyatt:~/wow$ wine wow.exe -opengl
fixme:midi:OSS_MidiInit Synthesizer support MIDI in. Not supported yet (please report)
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f5dc,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:wininet:InternetSetOptionW Option 45 STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_RECEIVE_TIMEOUT: STUB
fixme:opengl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9d058,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9d0b0,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:system:SystemParametersInfoW Un[/PHP]


Any help would be really appreciated. I copied the WoW files (and the expansion) from a windows computer, and used wine to run them here.

Thanks in advance!

---

### Post by skirkpatrick on 2007-02-01
Your problem is probably that WoW defaults to run using Direct3D instead of OpenGL.  Here's a howto on getting it to run using Wine (what you probably only need to do is change the config file): [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)

I'm running it successfully using Linux and Wine on 3 different machines.

---

### Post by cdevilrun on 2007-02-01
Yeah, go through the HowTo and then try and run. (Making sure you run it in OpenGL)
If there are still issues, read the tips, tweaks and troubleshooting. Most of the common errors are addressed there. 

There are several long threads here about fixes, and appdb.winehq.org is also a very good resource. Just keep at it, eventually it will run flawlessly and you can be extra happy about your Linux box.

---

### Post by xfaith on 2007-03-27
I have been running Ubuntu for about a year now.  I just now installed WoW with the install guide I found here.  I had been using Wine for other apps so I uninstalled it completely and recompile with patches as instructed.  I am running Nvidia drivers and using OpenGL.  Video and Sound work great.  Smooth as can be but with one major problem.

"CAN'T use my mouse to interact with people (though I see the mouse icon and can move it, just cant click and interact). I CAN click on spells and the minmap.  I can target enemies etc using the keyboard, but CAN'T target with the mouse."    

Any specific advice to fix this issue?  I am about to reinstall the whole works just to get Wow to run.  I really don't want to install XP just for this game.  

Any help is appreciated

XFaith

---

### Post by hikaricore on 2007-03-27
You don't need to patch/compile wine anymore about 95% of the time, just use the latest version of wine for ubuntu/debian.  I'm not going any further into this.

---

### Post by xfaith on 2007-03-27
> **hikaricore said:**
> You don't need to patch/compile wine anymore about 95% of the time, just use the latest version of wine for ubuntu/debian.  I'm not going any further into this.

You are correct!!! I deleted all remnence of version 0.9.6, which I complied via web instruction, and install the current supported verion 0.9.33 and everything works beatifully.  Didn't even have to install WoW again.  

Goes to show you, start simple then go complicated.

XFaith:guitar:

---

