---
title: "Diablo II Problem under Wine"
date: 2006-04-19
forum: Gaming &amp; Leisure
---

### Post by markr on 2006-04-19
I tried to methods of installing Diablo II, both appear to work until you run the game (Copying from my Windows Directly and direct install under wine).

I have the NVidia drivers installed from the Dapper repository and my Wine version is 0.9.9.

I've tried to run the video test under wine, but it comes back with no available modes.  Running the game gives me the error below :

markr@krynn:/media/cdrom0$ fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 0\Scsi Bus 0\Target Id 7\Logical Unit Id 0
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 1.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 1\Scsi Bus 0\Target Id 7\Logical Unit Id 0
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 2.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 7\Logical Unit Id 0
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd7e9a8)->(0x20022,00000011)
fixme:x11drv:X11DRV_DDHAL_CreatePalette stub
fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x7fd7e9a8)->(0x20022,00000011)
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)

Any thoughts?

Mark.

---

### Post by hezral on 2006-04-19
i ran Diablo2 without any problems a few weeks ago. maybe you could try wine 0.9.12 the latest one. after that i choose the D2D display after the video test. if i used D3D it will not work. hope that helps

---

### Post by trotski on 2006-04-19
I use the -d3d switch myself.  I get full 3D support.

---

### Post by markr on 2006-04-20
Managed to get it working last night using the -w option (I still get the errors in the terminal, but the game plays okay (with sound).

My only greivance is that the window is way too small to play the game properly.  Is there anyway to increase the size of the window the game plays in (I've tried the -res option, but all this does is change the resolution of the graphics, it doesn't actaully impact the size of the screen)

Thanks

Mark.

---

### Post by erk on 2006-08-27
I have LOD mostly working under Ubuntu 6.06 with Wine 0.9.20 package from this repository:  deb ```
http://wine.budgetdedicated.com/apt dapper main
```

I had a problem with my Thinkpad R52 telling X that it only supported 1024x768 despite me putting entires in for 800x600 and 640x480. Seems that the xorg.conf that was created on install lacked a couple of critical lines in the Monitor section: 

 HorizSync 30-120
 VertRefresh 50-120

Now the only problem that remains is I have no sound. I have tried OSS and ALSA in the winecfg with no luck. The sound system  works outside of Wine no problems.

Anyone got an idea where to look?

---

