---
title: "Counter Strike Resize and Crash"
date: 2006-09-05
forum: Gaming &amp; Leisure
---

### Post by Adventx on 2006-09-05
Ok I know theres about a thousand threads about CS and wine but I have yet to find one that fixes my current problem. I've already passed the tahoma font fix and the 26% crash and CS is installed on my system and I've checked .wine/c:/Program Files/Steam/SteamApps/user/counter-strike/cstrike and verified that all the files are there and where they should be. But when I try to load CS from the Games panel it does the " Preparing to Launch Game " screen and then changes my resolution to 640 x 480 and does nothing. This is what the terminal says:

```
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
fixme:d3d:IWineD3DImpl_FillGLCaps >>>>>>>>>>>>>>>>> 501 from extension detection @ directx.c / 753
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at the moment!
No ctx->FragmentProgram._Current!!
fixme:d3d:IWineD3DImpl_FillGLCaps >>>>>>>>>>>>>>>>> 501 from extension detection @ directx.c / 753
fixme:shdocvw:ViewObject_SetAdvise (0xd8cd0c0)->(1 00000002 0x1002018)
fixme:shdocvw:PersistStreamInit_InitNew (0xd8cd0c0)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0xd8cd0c0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0xd8cd0c0)->(ffffffff)
fixme:shdocvw:WebBrowser_put_Silent (0xd8cd0c0)->(ffffffff)
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0xd8cd0c0)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0xd8cd0c0)
fixme:shdocvw:OleObject_Close (0xd8cd0c0)->(1)
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
fixme:d3d:IWineD3DImpl_FillGLCaps >>>>>>>>>>>>>>>>> 501 from extension detection @ directx.c / 753
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x193430) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x192b08)->((nil),00000008)fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x192b08)->((nil),00000013)fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x192b08)->((nil),00000008)fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16No ctx->FragmentProgram._Current!!
X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  17 (X_GLXVendorPrivateWithReply)
  Serial number of failed request:  508398
  Current serial number in output stream:  508398



```

I've tried -fullscreen -height 1024 -width 768 in launch options and that does nothing at all. Please help me :(

---

### Post by Adventx on 2006-09-05
BTW I'm using Wine 0.9.20 on Ubuntu 6.06 Drapper if that helps at all.

---

### Post by Adventx on 2006-09-05
bump

---

### Post by Adventx on 2006-09-05
If nobody knows anything about this than can somebody please tell me another place I can look to try to fix this?

---

### Post by Adventx on 2006-09-05
x

---

### Post by slimdog360 on 2006-09-06
> **Adventx said:**
> 
```

X Error of failed request:  GLXUnsupportedPrivateRequest
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  17 

```

Id say that its your hardware, that opcode failure is talking about the layout of your hardware and Im assuming how the drivers 'talk' to it. You might be able to get it working with different c# compilers/drivers/hardware.

If you don't have the latest drivers,you should try them. If you don't have the propriety drivers installed then Id say that could be your problem (or one of them).
I know this doesn't help you much but you seem to really be desperate for some sort of an answer.

---

### Post by Adventx on 2006-09-06
Well thank you for replying, I had CS running on FC5 when it was installed ( although it was unplayable due to massive loss and 4fps ) but Unbuntu seems to be doing just fine with the current drivers but it couldnt hurt to try to update them and give it a shot.

---

### Post by Adventx on 2006-09-06
Amazingly this has worked, I just now got CS to load and was playing just fine on a very busy server and still getting an average of 99 fps so I thank you very much.

---

### Post by cagefighter85 on 2006-09-13
wHAT EXTACTLY DOES THAT MEAN... i DONT KNOW THAT MUCH ABOUT COMPS. SAME THING HAPPENS TO ME.. BUT MINE DOESNT CRASH... ANY HELP WOULD BE GREAT!

---

