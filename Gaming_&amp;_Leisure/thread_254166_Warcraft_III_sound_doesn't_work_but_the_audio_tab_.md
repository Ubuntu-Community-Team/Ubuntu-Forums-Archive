---
title: "Warcraft III sound doesn't work but the audio tab in winecfg has no errors"
date: 2006-09-09
forum: Gaming &amp; Leisure
---

### Post by etotehpii on 2006-09-09
Hi,

I'm not sure what has happened but my sound in warcraft III nolonger works.  I've eliminated all the errors that caused the audiotab to crash in winecfg.  I don't get any errors when I select the audiotab.  The audiotab has OSS selected and the other option set to Full.  I've donw the fix of rename /usr/lib/wine/winearts.drv.so to something like renaming /usr/lib/wine/winearts.drv.so.old.  The game plays perfectly minus the sound not working.  I get the following message from Warcraft III:
Unable to initialize base sound services, sound is disabled.


 ```
wine /home/username/.wine.0608302329/drive_c/"Program Files"/"Warcraft III"/"Warcraft III.exe" -opengl
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34f64c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f67c,0x00000000), stub!
fixme:xvidmode:X11DRV_XF86VM_SetCurrentMode Cannot change screen BPP from 32 to 16
username@username-desktop:~$ fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:imm:ImmAssociateContextEx (0x10028, (nil), 16): stub
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x3800001
  Serial number of failed request:  455
  Current serial number in output stream:  457
```
 
One other thing I've noticed is usually wine makes some weird little noise when it launaches an application, it no longer makes this noise.
Thanks

---

### Post by fatsheep on 2006-09-09
Have you tried entering this command into the terminal before you play?

> 
sudo killall esd


---

### Post by etotehpii on 2006-09-09
That, kind sir has did the trick!

Still got all those errors but the sound works.

I can live with those errors.;) 

Thanks

---

