---
title: "Mugen problems"
date: 2008-06-12
forum: Gaming &amp; Leisure
---

### Post by EvilSlayerX on 2008-06-12
[COLOR="DarkOrchid"]Okay, I want to run Winmugen in Linux using Wine.  Well, I got it to run, but this happens:

Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
Warning: the specified System directory L"c:\\windows\\system32" is not accessible.
fixme:win:EnumDisplayDevicesW ((null),0,0x33eab0,0x00000000), stub!
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1255e0)->((nil),00000008 )
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1255e0)->((nil),00000008 )
fixme:d3d:IWineD3DDeviceImpl_Release (0x12b118 ) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x129898 with type 1,WINED3DRTYPE_SURFACE
Loading button config for P1 joystick win.
Loading button config for P2 joystick win.
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12b870)->((nil),00000008 )
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x12b870)->((nil),00000008 )
fixme:d3d:IWineD3DDeviceImpl_Release (0x12baf0) Device released with resources still bound, acceptable but unexpected
fixme:d3d:dumpResources Leftover resource 0x16c180 with type 1,WINED3DRTYPE_SURFACE
Initializing keyboard.
Initializing sound...ok
Initializing graphics.
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x130a70)->(0x20024,00000008 )
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x130a70)->(0x20024,00000008 )
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x130a70)->(0x20024,00000008 )
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x130a70)->((nil),00000008 )

I replaced the 8 and ) together with 8 ) because otherwise this would happen: :cool:

Yes, Winmugen will run even after that, but it's not only really slow, the colors are way off as well.

If a moderator wants to move this topic to a different forum because I accidentally placed this in the wrong section, go ahead and do so.[/COLOR]

---

