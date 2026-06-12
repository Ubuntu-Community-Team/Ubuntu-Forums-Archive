---
title: "WoW in x64, crashing with OpenGL"
date: 2007-03-18
forum: Gaming &amp; Leisure
---

### Post by mrbrdo on 2007-03-18
I tried running World of Warcraft trough wine in a 32bit chroot (i am on 64bit edgy) and also without a chroot, using the ia32-libs.. I get the same result in both cases.
When i run in Direct3D mode, everything is very slow, and it doesn't seem to get past the loading screen (after i click "Enter World").
In OpenGL it doesn't even start, i get:
```
$ wine WoW.exe -opengl
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7e0c0000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7e0c0000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x34edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f544,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f530,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:win:EnumDisplayDevicesW ((null),0,0x34f04c,0x00000000), stub!
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  28 ()
  Serial number of failed request:  506
  Current serial number in output stream:  507

```

I use latest nvidia binary drivers for x86_64 from their site, installed using envy. glxgears other opengl apps run fine..
```
$ glxinfo | grep direct
direct rendering: Yes
```
(but in chroot i get No, but i have the same error even when i run outside chroot, and glxgears work in chroot).

My card: nVidia GeForce 7600 GS
I tried also disabling and enabling Composite Xorg extension but it is the same in both cases. I run in 24bit color depth. Sound works (only can try in D3D, because OpenGL won't start), but it's choppy, but i think it's because the framerate is also very low in D3D. I'm more interested into getting OpenGL running, anyways.
I tried reinstalling the drivers using envy (it purges old config also), but still same problem.

Thanks

---

### Post by mrbrdo on 2007-03-19
Also, i tried running some other Windows OpenGL applications in Wine and they work fine.

---

### Post by mrbrdo on 2007-03-19
fixed it, now runs fine in both opengl and directx. the key was installing the nvidia drivers in the chroot. because i don't use the Ubuntu packaged nvidia-glx, but binary nvidia drivers, there is a problem in a 32bit chroot, so you have to follow the instructions here:
[http://transgaming.org/forum/viewtopic.php?t=7388](http://transgaming.org/forum/viewtopic.php?t=7388)
as noted in the second post, instead of making the uname script you can simply apt-get install linux32 and do sudo linux32 sh NVIDIA... also remember to run nvidia tool with --no-kernel-module

regards!

---

### Post by RobinOfSweden on 2007-05-04
Does anyone know if this fix works for Feisty 64?
I have a problem with starting World of Warcraft with OpenGL getting a err:wgl: etcetcetc
found out that its a rather common problem!

Well it would be better if there was a 64 solution to it then using chroot (never liked the thought of it :S ). Still i am grasping at hairstrays so if this works i will take it and embrace it :D

---

### Post by Aetheric on 2007-05-19
I have a similar problem. WoW will not run under OpenGL, and in D3D I get 8fps at best in Outlands and two mouse cursors.

I think it'll fix itself if I get WoW running under OpenGL but so far no luck. If I use wine wow.exe -opengl the game hangs after I click Enter World and the loading bar gets to about 75%. Makes no difference if I change the Config.wtf file.

Here's the error list I get  from running the game with D3D:

> fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7cb70000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cb70000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33edd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f33c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5dc,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x165f78) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d9:IDirect3DDevice9Impl_CreateQuery (0x1642a8) call to IWineD3DDevice_CreateQuery failed
fixme:win:EnumDisplayDevicesW ((null),0,0x33f04c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not supported on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
err:d3d:state_multisampleaa Multisample antialiasing not supported by gl
fixme:reg:GetNativeSystemInfo (0x37400f40) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7af764b8) stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d058,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d0b0,0x00000000), stub!
fixme:d3d:IWineD3DVertexBufferImpl_PreLoad Too much declaration changes, stopping converting
fixme:imm:ImmAssociateContextEx (0x10024, (nil), 16): stub
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_ResourceReleased Vertex buffer released while bound to a state block, stream 0

And with openGL:

> fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:powrprof:DllMain (0x7cb70000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7cb70000, 0, (nil)) not fully implemented
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
fixme:reg:GetNativeSystemInfo (0x37400f40) using GetSystemInfo()
fixme:process:IsWow64Process (0xffffffff 0x7aea84b8) stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d058,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33d0b0,0x00000000), stub!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0

I don't know enough to understand any of this :(

I'm running it on:

Athlon 64 3000+
512MB RAM
64MB nVidia GeForce 4 440 Go
Wine version: 0.9.37
Ubuntu Feisty 7.04
nVidia drivers installed using Automatix2

Please help?

---

### Post by rjwboys on 2007-05-19
humm just to let yall know opengl works with a lower version of wine ex: wine 0.9.24

edit and yes i am running a 64 bit of ubuntu

---

### Post by Aetheric on 2007-05-20
Ok I got WoW running with Crossover, but my fps is terrible and I have graphics errors all over the place.

Any suggestions? Next thing I'm going to try is to reinstall the graphics drivers...

---

### Post by Aetheric on 2007-05-21
Update - got rid of Crossover and installed Cedega 6.0, everything is running great now :) I have something like 3-5 times the frame rate that I was getting in Windows XP and no problems at all.  So no more windows for me!

---

### Post by burt_57 on 2007-05-21
> **Aetheric said:**
> Update - got rid of Crossover and installed Cedega 6.0, everything is running great now :) I have something like 3-5 times the frame rate that I was getting in Windows XP and no problems at all.  So no more windows for me!

They charge you money for the program... hummm dont like it. :(
I was hoping it would be free.

---

