---
title: "Half life 2 episode 2, not saving settings"
date: 2008-02-18
forum: Gaming &amp; Leisure
---

### Post by Hoxzer on 2008-02-18
Wine version: wine-0.9.55-208-gfd67f32
Ubuntu version: 7.10

When I change my graphic/sound settings inside Half life 2 episode two my settings get reseted after a restart of the game. 

I have tried to boot same game on windows environment and settings do get saved but they still remain default in linux. So I'm pretty sure that config file for graphic settings is located somewhere else than in game dir unlike config.cfg is.
This indacates a permission issue but I can't seem to find out the location of the graphic config file (I have googled this without success).

My start command for half life 2 episode two
```
 cd /media/hdb6/HL2/half-life\ 2\ episode\ two/
wine hl2.exe -steam -game ep2 -applaunch 220 -novid -dxlevel 80

```

Wine output (*** means that same message is beeing repeated numerous times)
```

fixme:vxd:VXD_Open Unknown/unsupported VxD L"gdperf.vxd". Try setting Windows version to 'nt40' or 'win31'.
fixme:win:EnumDisplayDevicesW ((null),0,0x33e2f8,0x00000000), stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
fixme:ole:CoInitializeSecurity ((nil),-1,(nil),(nil),0,3,(nil),0,(nil)) - stub!
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x1
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found 1024x768x32 @60! (XRandR)
fixme:d3d9:D3DPERF_SetOptions (0x1) : stub
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x15d6f8) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x15d6f8) : stub
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x11d268d8) : pBox=0x33e174 stub
***
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x11d268d8) : pBox=0x33e174 stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x11d268d8) : pBox=0x33e1c8 stub
***
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x11d268d8) : pBox=0x33e1c8 stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x15d6f8) : stub
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
***
fixme:font:WineEngAddFontResourceEx Ignoring flags 10
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x15d6f8) : stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x11bfd350) : pBox=0x33e1e0 stub
***
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x11bfd350) : pBox=0x33e1e0 stub
fixme:process:IsWow64Process (0xffffffff 0x33e334) stub!
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x15d6f8) : stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x11bfbb48) : pBox=0x33e2d8 stub
***
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x11bfbb48) : pBox=0x33e2d8 stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x15d6f8) : stub
***
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x15d6f8) : stub
fixme:d3d_draw:depth_copy Not supported with fixed up depth stencil
***
fixme:d3d_draw:depth_copy Not supported with fixed up depth stencil
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x15d6f8) : stub
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1d9a2e20) : pBox=0x33de70 stub
***
fixme:d3d:IWineD3DVolumeImpl_LockBox (0x1d9a2e20) : pBox=0x33de70 stub
fixme:d3d_draw:depth_copy Not supported with fixed up depth stencil
***
fixme:d3d_draw:depth_copy Not supported with fixed up depth stencil
fixme:font:WineEngRemoveFontResourceEx :stub
****
fixme:font:WineEngRemoveFontResourceEx :stub
fixme:avifile:AVIFileExit (): stub!
Unable to remove f:\hl2\half-life 2 episode two\ep2\gamestats.log!

```

---

### Post by Hoxzer on 2008-02-18
update: after some research I found out that valve games save their graphic settings inside the registery ( HKEY_CURRENT_USER\Software\Valve\Source )

It is in such format that I dont know how to edit it.

---

### Post by Hoxzer on 2008-02-18
Update: updated to latest from gitt (wine-0.9.55-208-gfd67f32)

---

