---
title: "WoW won't launch; 1420N &amp;wWine"
date: 2007-09-14
forum: Dell  Ubuntu Support
---

### Post by ImNeat on 2007-09-14
I have read various threads about issues with running WoW through wine without success, but I have yet to come across a solution.

Both WoW and BC installed without problems, but when I launch the game nothing happens.  I get a segmentation fault.

Has anyone found a work around/solution to this problem, or have any suggestions?  Thanks in advance!



Output:
```
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7c800000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7c800000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreatePbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleasePbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyPbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryPbufferARB) - not found
fixme:win:EnumDisplayDevicesW ((null),0,0x33ed40,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f328,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f05c,0x00000000), stub!
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreatePbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleasePbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyPbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryPbufferARB) - not found
fixme:win:EnumDisplayDevicesW ((null),0,0x33f74c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x154238) : stub, simulating 64MB for now, returning 64MB left
Segmentation fault (core dumped)
```

---

### Post by hiro24 on 2007-09-15
This seems to be a known problem.  I have a 1420n also and I can't get wine to run wow either (from apt-get or source built, opengl or direct3d).  I've seen other posts elsewhere about ppl w/ Dell laptops who are also unable to get WoW to work.  I'm getting the same seg fault as you, btw.  I believe somebody said it was a problem w/ the drivers not being up to spec, but I'm not quite sure about that.

At any rate, the hardware should be more than capable of running it.  I'm sorry, but I don't have an answer for you.  Hopefully somebody will come up w/ something soon though, as we're in the same boat. :(

---

### Post by ImNeat on 2007-09-23
It seems that the problem is the integrated X3100 card's driver (which is open source).

Has anyone found a work-around yet?  Will this still be a problem in Gutsy?

---

