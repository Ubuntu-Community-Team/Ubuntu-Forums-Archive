---
title: "Gateway GM5084 Nightmare"
date: 2009-05-30
forum: Desktop Environments
---

### Post by WeaponsTheyFear on 2009-05-30
I can't begin to explain my night with this Gateway.  All sorts of problems trying like hell to get XP installed, but just not working.  This is a new PC too.  Ubuntu was the only thing that worked, and it runs incredibly fast.

Only small problem ( compared to others tonight, this is nothing ), is that is doesn't recognize my display so I am stuck at like 800x600 resolution.  I sudo gedit 'ed my xorg.conf in etc/X11 and added a few lines to give the modes, but still seeing nothing in the preferences / display settings.  Here's what was added...

Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
Default Depth 24
SubSection "Display"
Depth 24
Modes "1280x1024" "1024x768" "800x600:
EndSubSection
EndSection

Am I missing something here or can the unknown display be configured?  Is there any way to get my hands on drivers to fix this?

I have swapped over my Linksys wireless card to this Gateway so I could get online and do my Q/A through it, but last time I tried to connect the thing froze ( other computer used Xubuntu, didn't need anything special for the wireless card ).

Thanks for any help with this Gateway.

Update - This Gateway uses the Nvidia GT6100, but I am not able to access the restricted drivers for whatever reason, don't even see a way to access them.

Edit - Managed to get the NVidia removed and reinstalled, now it just keeps asking me to edit the Xorg or whatever for Nvidia.

---

