---
title: "WoW Slow as heck... 200m Radeon"
date: 2006-04-04
forum: Gaming &amp; Leisure
---

### Post by shane.reid on 2006-04-04
I have it running via Wine... but it is insanely slow.

I'm on a HP dv5000
1.8ghz AMD64 Turion (note, i am running 32-bit)
1gb RAM
128mb Radeon Express 200m
I am successfully using fglrx as my driver for X

Here is the terminal output as it starts up

```
shane@narnia:~/.wine/drive_c/Program Files/World of Warcraft$ wine WoW.exe -opengl
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c670000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c670000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9eedc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f448,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f6e8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f650,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f63c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:win:EnumDisplayDevicesW ((null),0,0x7fb9f158,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wgl:wglQueryPbufferARB unsupported WGL_PBUFFER_LOST_ARB (need glXSelectEvent/GLX_DAMAGED work)
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub
```

Anyone have any idea why it is so slow?  I changed the Config.wtf to use OpenGL as the gx

---

### Post by shane.reid on 2006-04-04
Anyone on this one... ?  I need a WoW fix!

---

### Post by Toxicity999 on 2006-04-04
Honestly, you performance is going to blow... on some configurations its played fine and tolerable, on most you get 60-70% playability of windows TOPS. It's fun to say you get it going on Linux but don't lose any playability just to say it, I would just say try troubleshooting for a little if you find any answers, then if no luck give in and dual boot. Good Luck.

---

### Post by shane.reid on 2006-04-04
When I say slow... mean, entirely unplayable, less than 1 fps at best

My system is more than adequate to play this in Linux from what I've seen other people pull it off with...

If anyone has any suggestions.. let me know, I've tried tthe wine with patches... didn't work either.

---

### Post by YokoZar on 2006-04-04
Does OpenGL work on your system?  If not, things might be being run in software mode.

For instance, do the GL* screen savers render anything, or are they black?

---

### Post by shane.reid on 2006-04-05
shane@narnia:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS 200M Series SW TCL Generic
OpenGL version string: 2.0.5695 (8.23.7)

shane@narnia:~$


That assures that it is hardware rendered, right?

---

### Post by Toxicity999 on 2006-04-05
Well thats saying the fglrx is working okay yea... well... working right in theory... how do native games work? If you don't have any grab something that's in 3d from the Repos... if that works well then obviously it's narrowed down to wine itself... Is it just the 3D layout in game thats sucky or both that and the UI? In the WoW helpfiles there are lots of compatibility commands you can add to you wtf config file for cards that aren't overly helpful... Also try some other 3D games that are known to have few issues in Wine. Just get an idea where the problem is... in Your global OS configuration, WINE itself, WoW itself, and so on.

---

### Post by snowpalmer on 2006-08-02
> **shane.reid said:**
> I have it running via Wine... but it is insanely slow.

I'm on a HP dv5000
1.8ghz AMD64 Turion (note, i am running 32-bit)
1gb RAM
128mb Radeon Express 200m
I am successfully using fglrx as my driver for X


I have the same issue on my laptop. (Compaq R4000, AMD64 (not turion), 1.25 gb ram, 128mb Radeon Express 200m)

Under windows I get about 30fps while under linux I get about 4-5fps.

I've tried just about everything to get it going faster but it seems to me that it's just not going to work. 

Snowpalmer

---

