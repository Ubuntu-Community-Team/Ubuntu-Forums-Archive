---
title: "Warcraft III issues"
date: 2007-08-27
forum: Gaming &amp; Leisure
---

### Post by melzanis on 2007-08-27
Hey Everyone, 
        I'm new to Linux/Ubuntu, therefore I'm also new to using 'wine'. For some time now I have been trying to get WarcraftIII to install (including wine, but now wine is installed from what I can tell). I finally got it to install, but now when I go to play the came. I get these error messages in the terminal:
warlock@warlock-desktop:~/c/Program Files/Warcraft III$ wine Warcraft\ III.exe
err:ole:CoCreateInstance apartment not initialised
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1b4fc8) : stub, simulating 64MB for now, returning 64MB left
warlock@warlock-desktop:~/c/Program Files/Warcraft III$ fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(800x600x32)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(800x600x32)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(800x600x32)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(800x600x32)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(800x600x24)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(800x600x24)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(800x600x24)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(800x600x24)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(640x480x32)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(640x480x32)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(640x480x32)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(640x480x32)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(640x480x24)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(640x480x24)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(640x480x24)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(640x480x24)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(800x600x16)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(800x600x16)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(800x600x16)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(800x600x16)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(640x480x16)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(640x480x16)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(640x480x16)! (NoRes)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found(640x480x16)! (NoRes)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:quartz:AVISplitter_InputPin_PreConnect process ODML header
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1210020) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1c6088)->((nil),00000008)
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:mpeg3:MPEG3_StreamSize misses the block header overhead
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b4-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:AsyncReader_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:Parser_QueryInterface No interface for {56a868b5-0ad4-11ce-b03a-0020af0ba770}!
fixme:quartz:PullPin_Seek (0x1b34c0)->(000000000, 7fffffffffffffff)
fixme:quartz:PullPin_BeginFlush (0x1b34c0)->()
fixme:quartz:PullPin_EndFlush (0x1b34c0)->(

I have no idea what to do. Can some one please give me a hand in solving this issue. 

thanks

---

### Post by melzanis on 2007-08-27
NVM I fixed it :P
It was just a simple adjustment of the screen Res. just make sure you make the Res no smaller then 800x600

Cheers

---

