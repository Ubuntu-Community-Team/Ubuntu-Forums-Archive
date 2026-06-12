---
title: "Problems with Video display"
date: 2009-04-27
forum: General Help
---

### Post by steveomcd on 2009-04-27
Hi,
I recently upgraded to 9.04 and everything was working fine however there was a slight flicker that I was trying to fix..... Unfortunately, I have made it worse! (see attached image) 

During the start up everything is fine on the display I even get the ubuntu logo with the progress bar moving along however once It gets past this point the screen is a total mess and I cant do anything.

From what I have been reading here I am thinking that I need to get the machine to boot into Xorg and try and fix this? any tips are welcome!

---

### Post by mb_webguy on 2009-04-27
That started as a "slight flicker"?  Wow.  You really *did* make it worse.

Not to worry.  That's what the recovery console is for.  At the GRUB menu, select the recovery option and boot into a console.  Then use the following commands to backup your xorg.conf file and open it for editing.```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
nano /etc/X11/xorg.conf
```Now look for the "Device" section.  On the "Driver" line, replace whatever it says with "vesa".  Now save and exit, and use the command "reboot" to reboot the computer.  Now login normally, and things should be back to something you can work with.

---

### Post by steveomcd on 2009-04-27
Thanks :) will give this a try.

---

### Post by steveomcd on 2009-04-28
> **mb_webguy said:**
> That started as a "slight flicker"?  Wow.  You really *did* make it worse.

Not to worry.  That's what the recovery console is for.  At the GRUB menu, select the recovery option and boot into a console.  Then use the following commands to backup your xorg.conf file and open it for editing.```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
nano /etc/X11/xorg.conf
```Now look for the "Device" section.  On the "Driver" line, replace whatever it says with "vesa".  Now save and exit, and use the command "reboot" to reboot the computer.  Now login normally, and things should be back to something you can work with.

Unfortunately I still have the same result as before after making this change.....
Too make sure I am doing this right.....this is what it says in nano:

Section "Device"
[INDENT]Identifier             "Configured Video Device"

[/INDENT]So I replaced the  "Configured Video Device" with "vesa" saved and rebooted....but no joy.... any other ideas?

---

### Post by ferchon03 on 2009-04-28
mb_webguy meant:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

---

### Post by steveomcd on 2009-04-28
> **ferchon03 said:**
> mb_webguy meant:

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Thanks, tried this also, saved and rebooted... still the same issue....:confused:

---

### Post by steveomcd on 2009-04-29
any one else with some tips to reset this?

---

### Post by steveomcd on 2009-05-05
help?

---

### Post by rohan21 on 2009-05-05
With display there can be just 2 issues :-

Monitor not detected properly and video driver not detected properly.

In 9.04 case i am sure video driver has been detected properly but not the monitor, check with your friends if they have the same monitor - you can use their monitor settings in your xorg.conf file and then reboot.

pasting the relevant section of my xorg.conf file. check this out if it helps.
----------------------------
Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "COMPAQ S710"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x1024 +0+0; 1024x768 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Regards
Rohan

---

### Post by wfp on 2009-05-05
Try rebooting back in recovery mode. Then from the recovery option menu> Choose Try to fix graphic problem that should undo the fixes you made. Once you boot back into the desktop enable your driver again.

---

### Post by steveomcd on 2009-05-10
> **rohan21 said:**
> With display there can be just 2 issues :-

Monitor not detected properly and video driver not detected properly.

In 9.04 case i am sure video driver has been detected properly but not the monitor, check with your friends if they have the same monitor - you can use their monitor settings in your xorg.conf file and then reboot.

pasting the relevant section of my xorg.conf file. check this out if it helps.
----------------------------
Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "COMPAQ S710"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6150"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x1024 +0+0; 1024x768 +0+0; 640x480 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Regards
Rohan

Thanks Rohan, I have been away but will try this tonight :)

---

### Post by steveomcd on 2009-05-10
> **wfp said:**
> Try rebooting back in recovery mode. Then from the recovery option menu> Choose Try to fix graphic problem that should undo the fixes you made. Once you boot back into the desktop enable your driver again.

Have tried this but no luck which was strange I thought....

---

