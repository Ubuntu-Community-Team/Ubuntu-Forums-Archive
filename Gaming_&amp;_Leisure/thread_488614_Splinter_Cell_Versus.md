---
title: "Splinter Cell Versus"
date: 2007-06-30
forum: Gaming &amp; Leisure
---

### Post by ppanag on 2007-06-30
Hello all.

I'm trying to figure out this wine thing to play this mode of the game. The thing about the Versus mode is that you don't need to install the game in order to play it. You just copy/paste the folder someone's installation and the game plays in ms windows. So, no worries for me about Starforce etc. The game is about 600mb with all the maps, so I can carry it in my usb stick and play on any pc with a card better than nv5xxx or ati9xxx, on windows.

I've followed some guides on the forum...
I've allowed pixel shaders emulation in the graphics tab of wine. 
I've set up emulation in the Audio tab, with 44100khz, 16bit, and driver emulation.

But when I try to run it using wine SCCT_Versus.exe I get this message:

> err:secur32:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
fixme:process:GetProcessWorkingSetSize (0xffffffff,0x34fb10,0x34fb0c): stub
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:system:SystemParametersInfoW Unimplemented action: 59 (SPI_SETSTICKYKEYS)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x19fea0) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d8:ValidatePixelShader (0x5ca74e8 (nil) 0 (nil)): stub
fixme:keyboard:RegisterHotKey (0x10030,49264,0x00000001,27): stub
fixme:keyboard:RegisterHotKey (0x10030,49265,0x00000001,9): stub
fixme:keyboard:RegisterHotKey (0x10030,49266,0x00000002,27): stub
fixme:keyboard:RegisterHotKey (0x10030,49267,0x00000002,9): stub
fixme:imm:ImmReleaseContext (0x10030, 0x160de0): stub
fixme:imm:ImmReleaseContext (0x10030, 0x160de0): stub
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:d3d_shader:vshader_set_limits Unrecognized vertex shader version 0
fixme:imm:ImmReleaseContext (0x10030, 0x160de0): stub
fixme:wave:widDsCreate DirectSoundCapture not implemented
fixme:wave:widDsCreate The (slower) DirectSound HEL mode will be used instead.
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported MAGFILTER* value 5, state 5
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges Unrecognized or unsupported D3DSAMP_MINFILTER value 5, state 6 D3DSAMP_MIPFILTER value 0, state 7
fixme:d3d_texture:IWineD3DBaseTextureImpl_ApplyStateChanges >>>>>>>>>>>>>>>>> 0x501 from glTexParameter GL_TEXTURE_MIN_FILTER, ... @ basetexture.c / 428
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
Mesa 6.5.2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
DRM_I830_CMDBUFFER: -22


The game uses the unreal engine, I can play it on low detail with my ilaptop's intel915 in windows. Please help, this is, more or less, the only game I play, and the only reason I have a windows installation on my laptop.

Thanks in advance!

---

