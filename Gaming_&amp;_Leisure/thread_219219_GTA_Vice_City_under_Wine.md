---
title: "GTA: Vice City under Wine"
date: 2006-07-19
forum: Gaming &amp; Leisure
---

### Post by Aurdal on 2006-07-19
Hey, I just installed GTA Vice City with the loki installer and I am running it under wine.

It seems to work ok, but well, many of the textures are mighty dark and the sound is jerky.

Anyway: While I play, my terminal is reporting the following:

```

fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE1,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE2,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE3,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_BLENDFACTOR ,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SRGBWRITEEN ABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SEPARATEALP HABLENDENABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SRCBLENDALP HA,2) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_DESTBLENDAL PHA,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_BLENDOPALPH A,1) not handled yet
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MULTISAMPLE MASK,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_PATCHEDGEST YLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_PATCHSEGMEN TS,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_DEBUGMONITO RTOKEN,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_POSITIONDEG REE,3) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_NORMALDEGRE E,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MINTESSELLA TIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MAXTESSELLA TIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_X,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_Y,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_Z,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_W,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ENABLEADAPT IVETESSELLATION,0) not handled yet
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE1,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE2,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE3,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_BLENDFACTOR ,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SRGBWRITEEN ABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SEPARATEALP HABLENDENABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SRCBLENDALP HA,2) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_DESTBLENDAL PHA,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_BLENDOPALPH A,1) not handled yet
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MULTISAMPLE MASK,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_PATCHEDGEST YLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_PATCHSEGMEN TS,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_DEBUGMONITO RTOKEN,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_POSITIONDEG REE,3) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_NORMALDEGRE E,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MINTESSELLA TIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MAXTESSELLA TIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_X,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_Y,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_Z,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_W,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ENABLEADAPT IVETESSELLATION,0) not handled yet
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE1,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE2,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE3,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_BLENDFACTOR ,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SRGBWRITEEN ABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SEPARATEALP HABLENDENABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SRCBLENDALP HA,2) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_DESTBLENDAL PHA,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_BLENDOPALPH A,1) not handled yet
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MULTISAMPLE MASK,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_PATCHEDGEST YLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_PATCHSEGMEN TS,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_DEBUGMONITO RTOKEN,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_POSITIONDEG REE,3) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_NORMALDEGRE E,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MINTESSELLA TIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MAXTESSELLA TIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_X,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_Y,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_Z,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_W,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ENABLEADAPT IVETESSELLATION,0) not handled yet
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE1,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE2,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE3,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_BLENDFACTOR ,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SRGBWRITEEN ABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SEPARATEALP HABLENDENABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SRCBLENDALP HA,2) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_DESTBLENDAL PHA,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_BLENDOPALPH A,1) not handled yet
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MULTISAMPLE MASK,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_PATCHEDGEST YLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_PATCHSEGMEN TS,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_DEBUGMONITO RTOKEN,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_POSITIONDEG REE,3) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_NORMALDEGRE E,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MINTESSELLA TIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MAXTESSELLA TIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_X,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_Y,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_Z,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_W,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ENABLEADAPT IVETESSELLATION,0) not handled yet
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE1,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE2,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE3,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_BLENDFACTOR ,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SRGBWRITEEN ABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SEPARATEALP HABLENDENABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SRCBLENDALP HA,2) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_DESTBLENDAL PHA,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_BLENDOPALPH A,1) not handled yet
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MULTISAMPLE MASK,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_PATCHEDGEST YLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_PATCHSEGMEN TS,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_DEBUGMONITO RTOKEN,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_POSITIONDEG REE,3) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_NORMALDEGRE E,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MINTESSELLA TIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_MAXTESSELLA TIONLEVEL,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_X,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_Y,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_Z,1065353216) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ADAPTIVETES S_W,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_ENABLEADAPT IVETESSELLATION,0) not handled yet
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilFunc Unrecognized D3DCMPFUNC value 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:StencilOp Unrecognized stencil op 0
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE1,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE2,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_COLORWRITEE NABLE3,15) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_BLENDFACTOR ,-1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SRGBWRITEEN ABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SEPARATEALP HABLENDENABLE,0) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_SRCBLENDALP HA,2) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_DESTBLENDAL PHA,1) not handled yet
fixme:d3d:IWineD3DDeviceImpl_SetRenderState (0x7fd8bf40)->(WINED3DRS_BLENDOPALPH A,1) not handled yet

```

Is this notmal, or is there an error with the D3D?

Thanks.
-Aurdal

---

### Post by vem0m on 2006-07-19
hehe yay for wines fixme strings lol i unno but it does that with most stuff i run thu wine so like i said i unno

---

