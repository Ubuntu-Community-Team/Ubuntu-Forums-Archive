---
title: "EAC/Wine..no CD drive?"
date: 2006-08-24
forum: Desktop Environments
---

### Post by Cable on 2006-08-24
I *used* to have EAC working perfectly in wine.  Now my cdrom drive shows up in winecfg, but not in EAC.  I have no clue how to get EAC to see my drive again.  Help?

---

### Post by Cable on 2006-08-24
Here is what happens when I start EAC in the terminal.  It opens the program fine, but there are no choices for cdrom drives available.
```

caleb@Cable:~/.wine/drive_c/Program Files/Exact Audio Copy$ wine EAC.exe 
ALSA lib pcm_dmix.c:762:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
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
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 0\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 7\Logical Unit Id 0
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 3.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 3\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 3\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 3\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 3\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 3\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 3\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 3\Scsi Bus 0\Target Id 7\Logical Unit Id 0
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 0.
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
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 0\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 2\Scsi Bus 0\Target Id 7\Logical Unit Id 0
fixme:aspi:SendASPI32Command ASPI: Partially implemented SC_HA_INQUIRY for adapter 3.
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 3\Scsi Bus 0\Target Id 1\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 3\Scsi Bus 0\Target Id 2\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 3\Scsi Bus 0\Target Id 3\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 3\Scsi Bus 0\Target Id 4\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 3\Scsi Bus 0\Target Id 5\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 3\Scsi Bus 0\Target Id 6\Logical Unit Id 0
err:aspi:SCSI_GetDeviceName Could not open HKLM\HARDWARE\DEVICEMAP\Scsi\Scsi Port 3\Scsi Bus 0\Target Id 7\Logical Unit Id 0
fixme:win:SetWindowTextA setting text "CD Title " of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "CD Artist " of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Year " of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Genre " of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "freedb " of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text " Various Artists " of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Load" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Save" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "New" of other process window (nil) should not use SendMessage
fixme:win:SetWindowTextA setting text "Delete" of other process window (nil) should not use SendMessage

```

---

### Post by Barbelos on 2006-08-25
This issue is present with EAC in Windows as well, if you don't have any ASPI drivers installed.

Adaptec has some publically available ones, so search for adaptec and aspi. they're mirrored loads of places. 
Such as here:
[http://www.afterdawn.com/software/cdr_software/cdr_tools/aspi.cfm]("http://www.afterdawn.com/software/cdr_software/cdr_tools/aspi.cfm")
As for how you install these in Wine I have no idea.

Still not sure why you'd want to use EAC in Ubuntu though, Sound-Juicer, KAudiocreator and several other great apps are available for the same purposes.

---

### Post by gnoshi on 2006-08-28
EAC simply has features that no other ripper for windows or linux has, such as:
C2 error correction.
CUEsheet extraction, including track pregaps.
Pre-track-1 leadin extraction.
AccurateRip Database integration
and so on and so forth.

Still, rubyripper seems to be on its way to competing with this. Mainly, it just needs the pregap handling and the cuesheet extraction. AccurateRip database integration, while nice, is not essential.

---

### Post by citizenkeith on 2006-10-27
> **gnoshi said:**
> EAC simply has features that no other ripper for windows or linux has


Ain't that the truth. Anybody who suggests using other Linux apps instead of EAC with Wine probably doesn't know anything about EAC. ;)

I had the same problem, and pretty much gave up. I either rip in Windows or use Rubyripper.

---

