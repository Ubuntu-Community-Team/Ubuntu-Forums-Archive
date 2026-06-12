---
title: "tempest 2000"
date: 2007-06-02
forum: Gaming &amp; Leisure
---

### Post by Cresho on 2007-06-02
I was playing gridwars 2 and remembered about the atari jaguar having something similar.  I have the original pc tempest 2000 but will only play on windows 95.  Then I ran into this. [http://typhoon.kuto.de/index.html](http://typhoon.kuto.de/index.html)  the guys says there will be a linux version soon.

Anyway, I downloaded the windows version and it is just totally awsome!  it play super on my xp machine but since I rarely turn that on, I decided to run it in wine!  Guess what!!!! it runs....................sort of!.

If anybody can figure out what goes on with it under wine, please post!

---

### Post by hikaricore on 2007-06-02
I was checking LinuxEmu: [http://linuxemu.retrofaction.com/](http://linuxemu.retrofaction.com/)

And came across this: (Link to Virtual Jaguar GCC/SDL at the bottom of the list)
[http://linuxemu.retrofaction.com/links.php?category=Atari+Computer+%26+Videogame&page=2](http://linuxemu.retrofaction.com/links.php?category=Atari+Computer+%26+Videogame&page=2)

Which then led me to here:
[http://sdlemu.ngemu.com/index.php](http://sdlemu.ngemu.com/index.php)

And after finding little metion of VirtualJaguar on the above page I wound up here:
[http://icculus.org/virtualjaguar/](http://icculus.org/virtualjaguar/)

And towards the middle of the page, a link to a source archive:
[http://icculus.org/virtualjaguar/tarballs/virtualjaguar-1.0.7-src.tar.bz2](http://icculus.org/virtualjaguar/tarballs/virtualjaguar-1.0.7-src.tar.bz2)

You'll need to compile it on your own, search around for info on this.  ^_^

Hopefully this isn't a dead end for the wild goosechase I've just been on hehe.

---

### Post by Cresho on 2007-06-02
yeah I can play those just fine on my zaurus c-3200.  Runs all the oldschool consoles emulated.  I have the original Tempest 2000 pc version which will not run on my system at all even on me or windows xp.  Interplay went out with a small bang and Im stuck.  I found typhoon 2001 which is way beyond what i expected out of a free game and can barely run it in wine.  hmmm....wine just got updated.

---

### Post by hikaricore on 2007-06-02
> **Cresho said:**
> hmmm....wine just got updated.

I could have easily told you that much ^_^

[http://gaming.gwos.org/comment.php?comment.news.91](http://gaming.gwos.org/comment.php?comment.news.91)

---

### Post by Cresho on 2007-06-02
I'm putting this out in an attempt to find an answer.  anyway, I launched it with the icon i created and it goes full screen and then it gives me an error that it cannot find a certain file in a certain directory related to the game in this form "cannot find ./game/default/some.web" file.  If i launch it in a previous version of wine, it runs from the file browser but it stutters like crazy.  It does play!  it just needs tweeking.


```
lubna@lubna-desktop:~$ WINEDEBUG=warn+heap wine "c:\\Program Files\T2K1\typhoon.exe"
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x16cdb8) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16c128)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x16c128)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:d3d:IWineD3DDeviceImpl_Release (0x16cdb8) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x1bc268 with type 1,WINED3DRTYPE_SURFACE
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:wave:DSD_CreateSecondaryBuffer (0x1a7200,0xbefad0,18080,0,0x1b7bac,0x1b7cbc,0x1b7b88): stub
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
err:wgl:X11DRV_wglGetProcAddress (wglGetPixelFormatAttribivEXT) - not found
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2016 WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2018 WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 201a WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 201c WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 201d WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 201e WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 201f WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2020 WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2021 WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2016 WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2018 WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 201a WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 201c WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 201d WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 201e WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 201f WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2020 WGL Attribute
fixme:wgl:X11DRV_wglGetPixelFormatAttribivARB unsupported 2021 WGL Attribute
fixme:system:SystemParametersInfoW Unimplemented action: 8192 (SPI_GETFOREGROUNDLOCKTIMEOUT)
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
fixme:system:SystemParametersInfoW Unimplemented action: 8193 (SPI_SETFOREGROUNDLOCKTIMEOUT)
err:wgl:X11DRV_wglGetProcAddress (wglCreateBufferRegionARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDeleteBufferRegionARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglSaveBufferRegionARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglRestoreBufferRegionARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglBindTexImageARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleaseTexImageARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreateDisplayColorTableEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglLoadDisplayColorTableEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglBindDisplayColorTableEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyDisplayColorTableEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreatePbufferEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPbufferDCEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleasePbufferDCEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyPbufferEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryPbufferEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPixelFormatAttribivEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPixelFormatAttribfvEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglChoosePixelFormatEXT) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetSyncValuesOML) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetMscRateOML) - not found
err:wgl:X11DRV_wglGetProcAddress (wglSwapBuffersMscOML) - not found
err:wgl:X11DRV_wglGetProcAddress (wglSwapLayerBuffersMscOML) - not found
err:wgl:X11DRV_wglGetProcAddress (wglWaitForMscOML) - not found
err:wgl:X11DRV_wglGetProcAddress (wglWaitForSbcOML) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetDigitalVideoParametersI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglSetDigitalVideoParametersI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetGammaTableParametersI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglSetGammaTableParametersI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetGammaTableI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglSetGammaTableI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglEnableGenlockI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDisableGenlockI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglIsEnabledGenlockI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGenlockSourceI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetGenlockSourceI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGenlockSourceEdgeI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetGenlockSourceEdgeI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGenlockSampleRateI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetGenlockSampleRateI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGenlockSourceDelayI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetGenlockSourceDelayI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryGenlockMaxSourceDelayI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreateImageBufferI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyImageBufferI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglAssociateImageBufferEventsI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleaseImageBufferEventsI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglEnableFrameLockI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDisableFrameLockI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglIsEnabledFrameLockI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryFrameLockMasterI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetFrameUsageI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglBeginFrameTrackingI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglEndFrameTrackingI3D) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryFrameTrackingI3D) - not found
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1b7b60
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26876)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26812)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26748)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26748)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26748)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26748)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26748)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26748)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26748)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26748)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26748)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26684)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26684)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26684)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26684)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26684)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26684)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26684)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26684)
fixme:dsound:DSOUND_MixOne problem with underrun detection (mixlen=24576 < primary_done=26684)
wine: Unhandled page fault on write access to 0x00002a84 at address 0x401f32 (thread 0009), starting debugger...
Unhandled exception: page fault on write access to 0x00002a84 in 32-bit code (0x00401f32).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:00401f32 ESP:00bed150 EBP:00bed1d8 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:00bed160 ECX:3f000000 EDX:3f800000
 ESI:00000000 EDI:00000000
Stack dump:
0x00bed150:  00bed160 00000064 004dd1ed 0050b320
0x00bed160:  61672f2e 642f656d 75616665 742f746c
0x00bed170:  656c7469 6265772e ffffff00 7bc7c4b8
0x00bed180:  00004100 00000000 00bed198 7bc29887
0x00bed190:  7db29520 7db26544 00bed1a8 7db02140
0x00bed1a0:  7db29520 7dd0d980 00bed1d8 7dcf48e6
Backtrace:
=>1 0x00401f32 in typhoon (+0x1f32) (0x00bed1d8)
  2 0x004020c3 in typhoon (+0x20c3) (0x00befd58)
  3 0x00407667 in typhoon (+0x7667) (0x00befdf8)
  4 0x00458be8 in typhoon (+0x58be8) (0x0016b248)
  5 0x00000000 (0x00169a99)
  6 0x72676f72 (0x505c3a63)
  7 0x00000000 (0x00000000)
0x00401f32: movl        %ecx,0x2a84(%eax)
Modules:
Module  Address                 Debug info      Name (78 modules)
PE        400000-  9d2000       Export          typhoon
ELF     7b800000-7b929000       Deferred        kernel32<elf>
  \-PE  7b820000-7b929000       \               kernel32
ELF     7bc00000-7bc98000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc98000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7d188000-7d24e000       Deferred        wined3d<elf>
  \-PE  7d1a0000-7d24e000       \               wined3d
ELF     7d24e000-7d263000       Deferred        midimap<elf>
  \-PE  7d250000-7d263000       \               midimap
ELF     7d263000-7d289000       Deferred        msacm32<elf>
  \-PE  7d270000-7d289000       \               msacm32
ELF     7d289000-7d2c5000       Deferred        wineoss<elf>
  \-PE  7d290000-7d2c5000       \               wineoss
ELF     7d525000-7d53d000       Deferred        msacm32<elf>
  \-PE  7d530000-7d53d000       \               msacm32
ELF     7d53f000-7d544000       Deferred        libxfixes.so.3
ELF     7d544000-7d54d000       Deferred        libxcursor.so.1
ELF     7d54d000-7d56a000       Deferred        imm32<elf>
  \-PE  7d550000-7d56a000       \               imm32
ELF     7d56a000-7d570000       Deferred        libxrandr.so.2
ELF     7d570000-7d578000       Deferred        libxrender.so.1
ELF     7d578000-7d57b000       Deferred        libxinerama.so
ELF     7daa1000-7db30000       Deferred        winex11<elf>
  \-PE  7dab0000-7db30000       \               winex11
ELF     7dbc8000-7dbe8000       Deferred        libexpat.so.1
ELF     7dbe8000-7dc13000       Deferred        libfontconfig.so.1
ELF     7dc13000-7dc27000       Deferred        libz.so.1
ELF     7dc27000-7dc92000       Deferred        libfreetype.so.6
ELF     7dc92000-7dd13000       Deferred        opengl32<elf>
  \-PE  7dcb0000-7dd13000       \               opengl32
ELF     7dd13000-7dd7a000       Deferred        msvcrt<elf>
  \-PE  7dd20000-7dd7a000       \               msvcrt
ELF     7dddd000-7e663000       Deferred        libglcore.so.1
ELF     7e663000-7e6e3000       Deferred        libglu.so.1
ELF     7e6e3000-7e76f000       Deferred        libgl.so.1
ELF     7e76f000-7e785000       Deferred        glu32<elf>
  \-PE  7e780000-7e785000       \               glu32
ELF     7e785000-7e814000       Deferred        winmm<elf>
  \-PE  7e790000-7e814000       \               winmm
ELF     7e814000-7e85d000       Deferred        dsound<elf>
  \-PE  7e820000-7e85d000       \               dsound
ELF     7e85d000-7e893000       Deferred        dinput<elf>
  \-PE  7e870000-7e893000       \               dinput
ELF     7e893000-7e8a6000       Deferred        libresolv.so.2
ELF     7e8a6000-7e8c4000       Deferred        iphlpapi<elf>
  \-PE  7e8b0000-7e8c4000       \               iphlpapi
ELF     7e8c4000-7e919000       Deferred        rpcrt4<elf>
  \-PE  7e8d0000-7e919000       \               rpcrt4
ELF     7e919000-7e925000       Deferred        libgcc_s.so.1
ELF     7e934000-7e936000       Deferred        libnvidia-tls.so.1
ELF     7ea20000-7eae0000       Deferred        gdi32<elf>
  \-PE  7ea40000-7eae0000       \               gdi32
ELF     7eae0000-7ec1d000       Deferred        user32<elf>
  \-PE  7eb00000-7ec1d000       \               user32
ELF     7ec1d000-7ec65000       Deferred        advapi32<elf>
  \-PE  7ec30000-7ec65000       \               advapi32
ELF     7ec65000-7ed04000       Deferred        ole32<elf>
  \-PE  7ec70000-7ed04000       \               ole32
ELF     7ed04000-7ed09000       Deferred        libxdmcp.so.6
ELF     7ed09000-7edfa000       Deferred        libx11.so.6
ELF     7edfa000-7ee08000       Deferred        libxext.so.6
ELF     7ee08000-7ee0d000       Deferred        libxxf86vm.so.1
ELF     7ee0d000-7ee25000       Deferred        libice.so.6
ELF     7ee25000-7ee2e000       Deferred        libsm.so.6
ELF     7ee2e000-7ee81000       Deferred        ddraw<elf>
  \-PE  7ee40000-7ee81000       \               ddraw
ELF     7ef93000-7ef9e000       Deferred        libnss_files.so.2
ELF     7ef9e000-7efa8000       Deferred        libnss_nis.so.2
ELF     7efa8000-7efbf000       Deferred        libnsl.so.1
ELF     7efbf000-7efc8000       Deferred        libnss_compat.so.2
ELF     7efc8000-7efef000       Deferred        libm.so.6
ELF     7eff0000-7eff3000       Deferred        libxau.so.6
ELF     b7d34000-b7d38000       Deferred        libdl.so.2
ELF     b7d38000-b7e79000       Deferred        libc.so.6
ELF     b7e79000-b7e90000       Deferred        libpthread.so.0
ELF     b7ea1000-b7fb5000       Deferred        libwine.so.1
ELF     b7fb7000-b7fd2000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
00000008 (D) C:\Program Files\T2K1\typhoon.exe
        00000024   15
        00000011   15
        0000000f    0
        0000000e   15
        0000000d    1
        00000009    0 <==
lubna@lubna-desktop:~$ 

```

---

### Post by Cresho on 2007-06-02
a small update.  I can launch the game with the newer wine.  it runs fast but still i have some audio problems.  I had to disable beryl to metacity.  It runs but man it just needs a small tweak!>  the game will not launch from the icon.  It will launch from winefile and double clicking on the typhoon.exe within the program files of the windows.

---

### Post by hikaricore on 2007-06-02
It probably won't launch from the icon if there are other files aside from the main binary.
As you are trying to launch the exe file from outside it's directory, these files are not being found.

You could make a simple bash script like such:

(launcher.sh)
> #! /bin/bash
cd ~/.wine/drive_c/Program\ Files/WhateverFolderItsIn
WINEDEBUG=fixme-all,err-all,-all **wine filename.exe**


You'll need to: *chmod +x launcher.sh*
To make this script work.

Change the directory to match where it's located, and replace filename.exe with the actual filename.

The WINEDEBUG section should disable all error output, this may be causing some of your audio problems.

You can then link your desktop (our menu) launcher to this script and hopefully get results.

Aside from that, launch:

> winecfg

And try changing the audio output between the various options, close winecfg, and try launching your game again.  Aside from that see if your game supports any other audio output format through a config file or another method.

Hope this helps and good luck ^_^

--Aaron

---

### Post by cesium062 on 2007-06-03
I'm having similar problems.  Installed Fiesty Fawn today.  Installed latest wine via synoptics.  I have the known Unix cursor overlaps gloved cursor in this release of wine with WoW.

The first time I ran WoW, wine told me to turn on hardware sound emulation.  I did that.  When I run wine, I'm connected to the server.  I select my character and click on 'enter world'.  The bar crosses the bottom of the screen and the speakers make clicking sounds.  I get the sound underrun error spewing out of Wine.  Wine is consuming about 90% of the cpu; the system is consuming about 80% of the cpu, and WoW is consuming about 10% of the cpu.  (No, those aren't supposed to add up to 100% -- Wine+Wow equals 100%, about 80% is being done in sys and 20% in user land.)

The OSS driver is checked in winecfg.  What are the best settings to use for audio in winecfg?

My chip is 
model name      : Intel(R) Pentium(R) 4 CPU 2.53GHz
stepping        : 4
cpu MHz         : 2533.372

I have some sort of Nvidia graphics card.


What do the sound underrun errors mean?  Is Wine simply running too slow to be able to write the bits fast enough?  If I use a really small buffer does that help?  Is trying to emulate sound somehow wrong?  Is there a sound driver missing?

---

### Post by hikaricore on 2007-06-03
The best audio settings for wine vary from program to program.

I suggest posting these questions in an existing WoW thread, as your issue is only vaguely related to the OPs problem.
In the future please avoid "threadjacking".

---

### Post by AndrewRiedi on 2007-06-04
> **cesium062 said:**
> I'm having similar problems.  Installed Fiesty Fawn today.  Installed latest wine via synoptics.  I have the known Unix cursor overlaps gloved cursor in this release of wine with WoW.

The first time I ran WoW, wine told me to turn on hardware sound emulation.  I did that.  When I run wine, I'm connected to the server.  I select my character and click on 'enter world'.  The bar crosses the bottom of the screen and the speakers make clicking sounds.  I get the sound underrun error spewing out of Wine.  Wine is consuming about 90% of the cpu; the system is consuming about 80% of the cpu, and WoW is consuming about 10% of the cpu.  (No, those aren't supposed to add up to 100% -- Wine+Wow equals 100%, about 80% is being done in sys and 20% in user land.)

The OSS driver is checked in winecfg.  What are the best settings to use for audio in winecfg?

My chip is 
model name      : Intel(R) Pentium(R) 4 CPU 2.53GHz
stepping        : 4
cpu MHz         : 2533.372

I have some sort of Nvidia graphics card.


What do the sound underrun errors mean?  Is Wine simply running too slow to be able to write the bits fast enough?  If I use a really small buffer does that help?  Is trying to emulate sound somehow wrong?  Is there a sound driver missing?

I got my D3D HW cursor patch accepted into Wine-0.9.38.  Please enable it in WoW's settings to get rid of the double cursor issue.

---

### Post by hikaricore on 2007-06-04
> **AndrewRiedi said:**
> I got my D3D HW cursor patch accepted into Wine-0.9.38.  Please enable it in WoW's settings to get rid of the double cursor issue.

uggg.... replied in the wrong thread,

re-replied here: [http://ubuntuforums.org/showthread.php?p=2777596#post2777596](http://ubuntuforums.org/showthread.php?p=2777596#post2777596)

---

