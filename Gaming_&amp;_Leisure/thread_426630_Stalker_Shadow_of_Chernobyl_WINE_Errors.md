---
title: "Stalker Shadow of Chernobyl WINE Errors"
date: 2007-04-28
forum: Gaming &amp; Leisure
---

### Post by DennShin on 2007-04-28
Hi, Guys. 
  Still pretty new to linux but I am willing to learn if someone with more knowledge of programming/wine could help me pick these errors apart I would appreciate it. 

```

fixme:reg:GetNativeSystemInfo (0x34fea0) using GetSystemInfo()

fixme:process:IsWow64Process (0xffffffff 0x34fe9c) stub!

fixme:advapi:CheckTokenMembership ((nil) 0x192cc8 0x34fe1c) stub!

fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0xb20020) : stub, simulating 64MB for now, returning 64MB left

fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1a7a28)->((nil),00000008)

fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock

fixme:win:EnumDisplayDevicesW ((null),0,0x34e774,0x00000000), stub!

wine: Call from 0x7b842690 to unimplemented function shell32.dll.SHPathPrepareForWriteA, aborting

``` 

From what I have read the game is supposed to install and run out of the box albeit a few glitches but I seem to be unable to even install it.

---

### Post by justin whitaker on 2007-04-29
It's listed as Bronze at WineHQ, which means it runs, barely, not it runs out of the box with a few glitches. I think that is silver level. 

[http://appdb.winehq.org/appview.php?iVersionId=7377](http://appdb.winehq.org/appview.php?iVersionId=7377)

From the sounds of it, DX9 textures are not working, among other things, and the sound is flakey. It should run though in DX8 mode.

---

