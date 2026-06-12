---
title: "Yu-Gi-Oh! Power of Chaos Joey the Passion problem"
date: 2006-10-17
forum: Gaming &amp; Leisure
---

### Post by Edska on 2006-10-17
Hello.
Here is my problem. 
I installed wine and Joey. When I run Joey I only see black screen in wine.
Here s wine output:

```


edska@edska-desktop:~/.wine/drive_c/Program Files/Joey$ wine joey_pc.exe -win -nosound fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x168d80) : stub, simulating 64MB for now, returning 64MB left
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x168558)->(0x10024,00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x168558)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock


```

I am executing it with two commands -win -nosound. -win plays it in windowed mode and -nosound plays without sound. Without these two commands I can't even get to load Joey.

game crashes at this line:
```
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel 0x168558)->(0x10024,00000008)
```

when I hit close than these two lines adds in terminal:
```
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x168558)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock

```

I am using Geforce2 MX 64MB and it works great, bu error is in DirectDraw.
Anyone knows how to fix it?
Thanx

---

### Post by evilghost on 2006-10-17
You need to use WineX-CVS, TransGaming's Cedega, or another DirectX capable WINE.

---

