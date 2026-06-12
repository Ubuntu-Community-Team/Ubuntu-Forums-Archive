---
title: "Using IP tables correctly?"
date: 2009-06-28
forum: Gaming &amp; Leisure
---

### Post by Paradoxfox93 on 2009-06-28
I'm trying to get Ragnarok Online wined and I'm using IP tables to workaround a bug...but I'm not sure it's right because I've seen several different people refer to the same part of the command with different numbers.  Specifically:
```
iptables -t nat -A OUTPUT -d **51**.0.0.0 -j DNAT --to <target.ip>
```
Specifically the emboldened numbers are different on three different accounts and I'm getting the idea that wine is somehow useing the wrong ip and we're working around it using iptables.  If it varies by user it would make sense that this would be interfering in the connection but I'm not sure how to diagnose what ip wine is using.  I run in terminal but i only get:
```
fixme:win:EnumDisplayDevicesW ((null),0,0x32f58c,0x00000000), stub!
fixme:d3d:WineD3D_ChoosePixelFormat Add OpenGL context recreation support to SetDepthStencilSurface
fixme:d3d_surface:surface_download_data Read back converted textures unsupported, format=WINED3DFMT_X8R8G8B8
fixme:d3d_surface:surface_download_data Read back converted textures unsupported, format=WINED3DFMT_X8R8G8B8
fixme:d3d_surface:surface_download_data Read back converted textures unsupported, format=WINED3DFMT_X8R8G8B8
fixme:d3d_surface:surface_download_data Read back converted textures unsupported, format=WINED3DFMT_X8R8G8B8
fixme:dinput:SysMouseAImpl_Acquire Clipping cursor to (80,60)-(726,565)
fixme:imm:ImmReleaseContext (0x10026, 0x136078): stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x17eda8)->(1,(nil)): Stub
###Repeats until closing the program
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x17eda8)->(1,(nil)): Stub
fixme:d3d_surface:IWineD3DBaseSurfaceImpl_Blt Can't handle WINEDDBLT_ASYNC flag right now.
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x17eda8)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x17eda8)->(1,(nil)): Stub
fixme:ddraw:IDirectDrawImpl_WaitForVerticalBlank (0x17eda8)->(1,(nil)): Stub
err:ole:CoUninitialize Mismatched CoUninitialize

```

---

