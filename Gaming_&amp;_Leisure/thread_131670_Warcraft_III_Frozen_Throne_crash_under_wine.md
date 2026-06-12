---
title: "Warcraft III: Frozen Throne crash under wine"
date: 2006-02-16
forum: Gaming &amp; Leisure
---

### Post by gt_momo on 2006-02-16
My favorite game keeps crashing on me under wine 0.9.8!

I am using wine Frozen\ Throne.exe -- -opengl

I am using latest nVidia drivers. 81.78 for linux -_-

What's going on?



window title: war3

content:```


This application has encountered a critical error:

FATAL ERROR!

Program: C:\Program Files\Warcraft III\war3.exe
Exception: 0xC0000005 (ACCESS_VIOLATION) at 0073:7BB055D7

The instruction at '0x7BB055D7' referenced memory at '0x00000008'.
The memory could not be 'read'.
```



And in the terminal here's the error:



```

fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:cursor:SetSystemCursor (0x112e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1146,00007f03),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11ce,00007f02),stub!
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:d3d:IWineD3DImpl_CreateDevice (0x7fe12148) Incomplete stub for d3d8
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x7b920020) : stub, emulating 64Mib for now, returning 64Mib
fixme:d3d_caps:IDirect3D8Impl_FillGLCaps found GL_VERSION  ("2.0.1 NVIDIA 81.78")->(0x00511ff2)
fixme:d3d_caps:IDirect3D8Impl_FillGLCaps found GL_RENDERER ("GeForce 6600 GT/AGP/SSE/3DNOW!")->(0x0250)
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x7fe12450)->(128,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x7fe12450)->(129,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x7fe12450)->(130,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x7fe12450)->(131,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x7fe12450)->(132,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x7fe12450)->(133,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x7fe12450)->(134,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x7fe12450)->(135,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x7fe12450)->(162,-1) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x7fe12450)->(163,0) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x7fe12450)->(164,1065353216) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x7fe12450)->(165,1) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x7fe12450)->(172,3) not handled yet
fixme:d3d:IDirect3DDevice8Impl_SetRenderState (0x7fe12450)->(173,1) not handled yet
fixme:dbghelp:sffip_cb NIY on 'E:\Drive1\temp\buildwar3x\War3\bin\Game.pdb'

```

---

### Post by gt_momo on 2006-02-17
OK. So I figured out the game doesn't crash if I set the default environment to Windows 98 BUT now Warcraft keeps on asking me for the CD! Here's the errors from the terminal:

```

fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 7\Logical Unit Id 0
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 7\Logical Unit Id 0

```

I have tried to tweak the registry settings to D:\ for the disc location and in winecfg D: has been set to both /dev/cdrom AND I've also tried /media/cdrom0. Whenever I use a NOCD exe from megagames.com the game gives me the same error as in my previous post.

---

### Post by gt_momo on 2006-02-17
OK.

I tried building wine from source with gcc 3.4 as was recommended by the wine HOWTO on Warcraft III (because gcc 4.0 breaks securom) BUT NOW here's my problem:

In terminal wine is giving me 4 "err:imagelist:ImageList_ReplaceIcon no color!" errors and also saying "Application tries to create a window, but no driver could be loaded. Make sure that your X server is running and that $DISPLAY is set correctly." anyone know what that's about? How would I go about setting $DISPLAY correctly, and what does it do?

---

### Post by gt_momo on 2006-02-17
newest batch of errors after figuring out how to get cd drive working!

fixme:ole:ITypeInfo_fnRelease destroy child objects
fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:cursor:SetSystemCursor (0x1126,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x112e,00007f00),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f03),stub!
fixme:cursor:SetSystemCursor (0x1146,00007f01),stub!
fixme:cursor:SetSystemCursor (0x1156,00007f88),stub!
fixme:cursor:SetSystemCursor (0x1166,00007f86),stub!
fixme:cursor:SetSystemCursor (0x1176,00007f83),stub!
fixme:cursor:SetSystemCursor (0x1186,00007f85),stub!
fixme:cursor:SetSystemCursor (0x1196,00007f82),stub!
fixme:cursor:SetSystemCursor (0x11a6,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11b6,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11c6,00007f02),stub!
err:ole:CoCreateInstance apartment not initialised
fixme:win:EnumDisplayDevicesW ((null),0,0x7fafef44,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7fafef7c,0x00000000), stub!
[email]aaron@ubuntu:~/.wine[/email]/drive_c/Program Files/Warcraft III$ fixme:win:EnumDisplayDevicesW ((null),0,0x7fafc900,0x00000000), stub!
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  465
  Current serial number in output stream:  465

---

### Post by essge on 2006-02-17
The error is due to a bug in either nvidia proprietary drivers or wine(probably nvidia). It occures when an application tries to change resolution, therefore start wc3 with "-window" and set it to use the same resolution as your desktop.

---

### Post by gt_momo on 2006-02-17
yep. you were right.

now i wonder if there's a way to specify resolution from the command line!

time to google...

---

### Post by meastp on 2006-02-18
Ok, I got the cd error too...

Therefore I tried to delete .wine and reinstall wc3 + wc3tft + 1.15 patch.

Then:

```
meastp@ubuntu:~/.wine/drive_c/Warcraft III$ wine war3 -opengl
err:ole:CoCreateInstance apartment not initialised
fixme:win:EnumDisplayDevicesW ((null),0,0x7faef64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x7faef67c,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 16 to 32fixme:win:EnumDisplayDevicesW ((null),0,0x7faed2d8,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 16 to 32X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  385
  Current serial number in output stream:  385
meastp@ubuntu:~/.wine/drive_c/Warcraft III$

```

Guess someone should file a bug at winehq... give me the bug number, and I'll vote for it.

EIDT: I just made a bug: [http://bugs.winehq.org/show_bug.cgi?id=4604](http://bugs.winehq.org/show_bug.cgi?id=4604)

---

### Post by clarke.rainey on 2006-10-08
I am getting the same error and crash as you, but I am running with the latest wine on edgy knot2, and FT 1.20e.  Right after install my game runs fine, but when I try to go into the options menu, it crashes right away and then refuses to start the game without a crash again... I am running it with the -opengl flag and I have tried it with the -window flag...

any suggestions?..

---

