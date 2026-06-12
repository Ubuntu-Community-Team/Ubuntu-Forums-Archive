---
title: "Problems with Cedega CVS"
date: 2006-06-11
forum: Gaming &amp; Leisure
---

### Post by dotinmouth on 2006-06-11
Hello guys

Yesterday i installed the cvs version of cedega with an script of linux-gamers. All looks to be ok but when i try to open a program i get always the same error:
```

doti@ubuntu:~$ cvscedega /media/hdc5/WoW/Installer.exe
fixme:cdrom:CDROM_GetIdeInterface not implemented for true scsi drives
wine: Unhandled exception, starting debugger...
err:seh:EXC_DefaultHandling Unhandled exception code c0000005 flags 0 addr 0xb7c6e855

```

What can i do?

Thanks

---

### Post by dotinmouth on 2006-06-11
There was a problem in the config file. Now i can run the installer but i have another error when the installer try to intall directx. Can someone show me a config file that works fine. Thanks

---

### Post by QuaintRealist on 2006-06-11
Wine vanilla (0.9.15) has made some major strides in directx of late, and I've had more success with that than with Cedega.  Currently playing Warcraft III and HOMM III and IV under vanilla Wine with no problems.  Depends on what games you're trying to play, of course...

---

### Post by dotinmouth on 2006-06-11
Now i get this error "WoW was unable to load 3d acceleration", and in the console i have this error:
```

doti@ubuntu:~/.cvscedega/drive_c/World of Warcraft$ cvscedega WoW.exe err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
fixme:keyboard:X11DRV_KEYBOARD_DetectLayout Your keyboard layout was not found!
Using closest match instead (Latin American keyboard layout) for scancode mapping.
Please define your layout in windows/x11drv/keyboard.c and submit them
to us for inclusion into future Wine releases.
See the Wine User Guide, chapter "Keyboard" for more information.
fixme:win32:PE_CreateModule Security directory ignored
fixme:win32:PE_CreateModule Load Configuration directory ignored
err:virtual:VirtualFree Could not remap pages, expect trouble
err:virtual:VirtualFree Could not remap pages, expect trouble
err:virtual:VirtualFree Could not remap pages, expect trouble
err:virtual:VirtualFree Could not remap pages, expect trouble
err:virtual:VirtualFree Could not remap pages, expect trouble
err:virtual:VirtualFree Could not remap pages, expect trouble
err:virtual:VirtualFree Could not remap pages, expect trouble
fixme:msvcrt:_fstat :dwFileAttributes = 32, mode set to 0
fixme:powrprof:DllMain (0xb39c7000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7ae1a08,0x00000000), stub!
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7ae1828,0x00000000), stub!
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7ae1dc4,0x00000000), stub!
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7ae1dc4,0x00000000), stub!
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7ae1530,0x00000000), stub!
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7ae1d30,0x00000000), stub!
fixme:system:SystemParametersInfoA Unknown action: 113
fixme:system:EnumDisplayDevicesA ((nil),0,0xb7ae1d1c,0x00000000), stub!
fixme:x11drv:X11DRV_DD_GetCurrentMode :stub
fixme:x11drv:X11DRV_DD_SetCurrentMode :stub
fixme:bitmap:CreateBitmap planes = 0
err:opengl:X11DRV_DescribePixelFormat Wrong pixel format !
fixme:opengl:wglGetPixelFormatAttribivARB stub
fixme:opengl:wglGetPixelFormatAttribivARB stub
fixme:opengl:wglGetPixelFormatAttribivARB stub
fixme:opengl:wglGetPixelFormatAttribivARB stub
err:virtual:VirtualFree Could not remap pages, expect trouble
err:virtual:VirtualFree Could not remap pages, expect trouble
err:virtual:VirtualFree Could not remap pages, expect trouble
err:virtual:VirtualFree Could not remap pages, expect trouble
err:virtual:VirtualFree Could not remap pages, expect trouble
err:virtual:VirtualFree Could not remap pages, expect trouble
fixme:powrprof:DllMain (0xb39c7000, 0, 0x1) not fully implemented
fixme:xrender:X11DRV_XRender_Finalize Free cached glyphsets

```

glxinfo:
```

doti@ubuntu:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: GeForce FX 5200/AGP/SSE2

```
When i run glxgear the gears are too slow (it's rare) and i don't get information about the fts in the cosole. I only get the message "X connection to :0.0 broken (explicit kill or server shutdown)." when i close the glxgear's window

What could be the problem?

---

### Post by seth0x2b on 2006-06-11
dotinmouth:
I don't use cedega so I'm not sure about this, but I think "unable to load 3d acceleration" is wow's "problem", not cedega's.
From your output it seems that you have direct rendering enabled so the drivers are probably ok. It doesn't matter that the gears are moving slow.They are moving slow on my machine also, but the FPS output is correct.Glxgears is not a benchmarking utility so you shouldn't rely to much on the result.To see the FPS output, just issue ```
glxgears -printfps
``` 

QuaintRealist:
Did HOMM IV install without any issues?! I remember trying it with wine 0.9.9 and failed, but now I have 0.9.15.
I'm gonna buy it if it works under WINE

Cheers

---

