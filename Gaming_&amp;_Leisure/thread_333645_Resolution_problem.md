---
title: "Resolution problem"
date: 2007-01-07
forum: Gaming &amp; Leisure
---

### Post by Iesos on 2007-01-07
Hi.
Trying to get wine working as usual. When running a game I get the following:

```

$ wine starcraft.exe 
fixme:advapi:SetSecurityInfo stub
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x172d80) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1725d0)->(0x10024,00000013)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1725d0)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock

```

and a messege from starcraft that it can't change resolution.
Ok, I know what the first reaction will be: Add 640x480 to your modes in xorg.conf. But guess what, I have allready done that (and restarted X). So it is something else. Anyone got any suggestions?

---

