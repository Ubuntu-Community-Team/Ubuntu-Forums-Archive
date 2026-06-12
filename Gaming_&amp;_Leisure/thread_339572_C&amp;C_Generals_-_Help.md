---
title: "C&amp;C Generals - Help"
date: 2007-01-16
forum: Gaming &amp; Leisure
---

### Post by tnunamak on 2007-01-16
I've been trying to get C&C generals working on Ubuntu. At first I had wine 0.9.29, and the game loaded but some textures were missing. Then something happened and now, the splash screen comes up, but I get the following output and then the game closes. I rolled wine back to 0.9.28, but the same thing still happens.

```
tnunamak@tnunamak:~$ wine '/home/tnunamak/.wine/drive_c/Program Files/EA Games/Command & Conquer The First Decade/Command & Conquer(tm) Generals Zero Hour/generals.exe'
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x5ca8028) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d8:IDirect3DDevice8Impl_CreateTexture (0x58e6370) call to IWineD3DDevice_CreateTexture failed
err:ole:CoGetClassObject class {2b2cc8b0-2dc0-48c6-b6fd-c07820a6477e} not registered
err:ole:CoGetClassObject class {2b2cc8b0-2dc0-48c6-b6fd-c07820a6477e} not registered
err:ole:create_server class {2b2cc8b0-2dc0-48c6-b6fd-c07820a6477e} not registered
err:ole:CoGetClassObject no class object {2b2cc8b0-2dc0-48c6-b6fd-c07820a6477e} could be created for context 0x7
fixme:imm:ImmGetDefaultIMEWnd (0x10026 - (nil) 0x1632f0 ): semi-stub
fixme:d3d8:ValidatePixelShader (0x2ee34c8 (nil) 0 (nil)): stub
fixme:d3d8:ValidatePixelShader (0x2915704 (nil) 0 (nil)): stub
fixme:d3d8:ValidatePixelShader (0x2ee34c8 (nil) 0 (nil)): stub
fixme:imm:ImmReleaseContext (0x10026, 0x1632f0): stub
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock

```

Any ideas?

Thanks

---

### Post by edemark on 2007-01-16
Hi you might try the loki installer. It worked for me though with cedega but it might work with wine to [http://liflg.org/?catid=7&gameid=21](http://liflg.org/?catid=7&gameid=21)

good luck

---

### Post by tnunamak on 2007-01-16
Thanks, I ran across that earlier but I can't use it because I'm installing from the C&C: The First Decade, which is a collection of all of the games. It can't find the correct path to install from.

---

### Post by m4sterblast3r on 2007-02-18
i've been tryin to install generals too, no luck. i always get stuck at 60% then error. i think this only works on cedega. :(    is there a list of popular pc games that work on wine, or crossover, i'd buy that if i could play Generals

---

### Post by balloons on 2007-03-23
Guys, I've had success with this working by ripping the cd to the drive and installing from there with wine version .9.33 (the latest as of this writing). i did need to add a msvicrt.dll to the folder - you may or may not. see if it complains

---

