---
title: "Guild Wars and 945GM"
date: 2007-09-18
forum: Gaming &amp; Leisure
---

### Post by thormania on 2007-09-18
Hey guys I'm trying trying to run guild wars on my laptop which uses a 945gm video chipset.

Basically it doesn't start correctly and heres what the console spits out when trying to load the game.


fixme:win:EnumDisplayDevicesW ((null),0,0x33f06c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:imm:ImmGetIMEFileNameA (0xc090c09, 0x790be2c8, 260): stub
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x132080) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x1800d8) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2c21230) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2f71440) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2f71230) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2c21230) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2c21700) : stub
fixme:wave:DSD_CreateSecondaryBuffer (0x28d1e58,0x790be674,100b4,0,0x3420128,0x2026bc,0x3420108): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x28d1e58,0x790be674,100e4,0,0x21201c0,0x28d1f04,0x21201a0): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x28d1e58,0x790be6a0,14,0,0x202720,0x34200c4,0x202700): stub
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
Mesa 6.5.2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
fixme:wave:DSD_CreateSecondaryBuffer (0x28d1e58,0x790be544,280b4,0,0x676f240,0x64cb57c,0x676f220): stub

So basically would could be the cause of this, or better still is there a fix?

Thanks for looking at my problem.

---

### Post by Ferrat on 2007-09-18
> **thormania said:**
> Hey guys I'm trying trying to run guild wars on my laptop which uses a 945gm video chipset.

Basically it doesn't start correctly and heres what the console spits out when trying to load the game.


fixme:win:EnumDisplayDevicesW ((null),0,0x33f06c,0x00000000), stub!
fixme:d3d:IWineD3DImpl_CheckDeviceMultiSampleType Quality levels unsupported at present
fixme:imm:ImmGetIMEFileNameA (0xc090c09, 0x790be2c8, 260): stub
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x132080) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x1800d8) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2c21230) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2f71440) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2f71230) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2c21230) : stub
fixme:d3d:IWineD3DResourceImpl_SetPriority (0x2c21700) : stub
fixme:wave:DSD_CreateSecondaryBuffer (0x28d1e58,0x790be674,100b4,0,0x3420128,0x2026bc,0x3420108): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x28d1e58,0x790be674,100e4,0,0x21201c0,0x28d1f04,0x21201a0): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x28d1e58,0x790be6a0,14,0,0x202720,0x34200c4,0x202700): stub
[B][COLOR="Red"]err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
Mesa 6.5.2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet[/COLOR][/B]
fixme:wave:DSD_CreateSecondaryBuffer (0x28d1e58,0x790be544,280b4,0,0x676f240,0x64cb57c,0x676f220): stub

So basically would could be the cause of this, or better still is there a fix?

Thanks for looking at my problem.

write the output of **glxinfo | grep direct**

I think the problem is the graficdriver

---

### Post by thormania on 2007-09-18
nmckay@Pancake:~$ glxinfo | grep direct
direct rendering: Yes

Thank you for the quick reply, i'd assume 3d is setup correctly from that?

---

### Post by Ferrat on 2007-09-18
> **thormania said:**
> nmckay@Pancake:~$ glxinfo | grep direct
direct rendering: Yes

Thank you for the quick reply, i'd assume 3d is setup correctly from that?

Yes, but then Im sorry to say, seems that your drivers isn't capable of 

```
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
Mesa 6.5.2 implementation error: i915_program_error: Exceeded max nr indirect texture lookups
Please report at bugzilla.freedesktop.org
err:d3d_draw:blt_to_drawable Blitting surfaces from sysmem not supported yet
```

this might pose a big problem if you can't find a driver capable of those things. I don't know for sure

---

