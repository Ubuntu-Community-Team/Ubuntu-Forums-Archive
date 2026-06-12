---
title: "Cedega Issues with World of Warcraft"
date: 2007-07-09
forum: Gaming &amp; Leisure
---

### Post by Denthral on 2007-07-09
[IMG]http://img461.imageshack.us/img461/9254/testsj7.png[/IMG]

Alright, I am sorry for the quality of the image but I seem to be having some problems with running WoW in Cedega, I have not installed any patches or anything as this is after a fresh install.

Here is my system info.

cpu: Intel(R) Pentium(R) 4 CPU 2.40GHz
cpu_ghz: 2.4
memory: 1010
videocard_manufacturer: Tungsten Graphics, Inc.
videocard_type: Mesa DRI R300 20060815 AGP 1x x86/MMX/SSE2 TCL
videocard_ram: 256
agp_aperture_size: N/A
videocard_driver_version: 1.3 Mesa 6.5.2
soundcard: SBLive! Value [CT4670] (rev.4, serial:0x201102) at 0xd880, irq 2
soundcard_driver: ALSA Version 1.0.13
machine_bitness: 32
kernel: 2.6.20-16-generic
x_version: Xorg Version 7.2.0
distro: Debian 4.0
GUI version: 6.0.2

Otherwise everything in the program is the same, I am running 6.0.2

The issue is that I am getting about 1 frame every 3 or so seconds and the black line in the actual image as you can see.

---

### Post by starcannon on 2007-08-18
I've got same card, its integrated in the inspiron 1420n (ubuntu). However I don't even get as far as you, cedega just crashes when I try to run WoW. Anyone able to get cedega/wow or wine/wow running on these intel gfx please help if you can.

---

### Post by cogadh on 2007-08-18
Have you tried following one of the how-to's:
[http://wowwiki.com/Linux/Wine](http://wowwiki.com/Linux/Wine)
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
Yes, they both talk about using Wine to run WoW, but all of the information except the Wine configuration applies to Cedega as well.

Also, have you tried Cedega's WoW forum? The answer may already be there:
[http://www.cedega.com/forum/viewforum.php?f=51](http://www.cedega.com/forum/viewforum.php?f=51)

---

### Post by eggplant37 on 2007-08-24
> **cogadh said:**
> Have you tried following one of the how-to's:
[http://wowwiki.com/Linux/Wine](http://wowwiki.com/Linux/Wine)
[https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft)
Yes, they both talk about using Wine to run WoW, but all of the information except the Wine configuration applies to Cedega as well.

Also, have you tried Cedega's WoW forum? The answer may already be there:
[http://www.cedega.com/forum/viewforum.php?f=51](http://www.cedega.com/forum/viewforum.php?f=51)

I, too, have had the same issue with a week-old Dell Inspiron 1402n, Intel 965G video chipset, and Feisty with xserver-xorg-video-intel 2:2.1.0-1ubuntu1 driver. This combination is impossible to get World of Warcraft, latest patch level as of 08/24/2007 up and running under either Wine or Cedega, latest versions available, whatsoever. Tweaking X and the game to any and every possible permutation on any and every webpage that I've ever been referred to results in the same thing:  X cycles through modelines in an attempt to change screen resolutions to something, Wine bitches about how it cannot change from 32 to 24 color depth (or 16 if set to 24 or 8 if set to 16, you get the point?), and the game bitches that it cannot set up 3D acceleration. 

I'm certain this game would play more than satisfactory under XP on the same laptop, and although I've not tried it specifically on my brand spankin' new Dell, it performs well enough on XP on my older Inspiron 2200. 

It's not a problem with the chipset; the chipset is perfectly capable of handling the graphics. The problem is with the drivers in combination with wine not taking full advantage of the chipset capabilities. The fact that the driver has only been out since May indicates to me that it's still very early in development and still has many bugs included and many features missing. 

Until the latest updates to X and the Intel driver are added to Feisty, it looks like us Dell purchasers who went on the cheap are going to suffer. I wonder if Dell will take this machine back and exchange it for one with a better chipset?

---

### Post by hikaricore on 2007-08-24
> **eggplant37 said:**
> Until the latest updates to X and the Intel driver are added to Feisty, it looks like us Dell purchasers who went on the cheap are going to suffer. I wonder if Dell will take this machine back and exchange it for one with a better chipset?

The intel chipset is integrated into the motherboard.  If this is a desktop system then you're best going with a PCIe or AGP Nvidia card.  If this is a laptop, you'd have to get an entirely new one with an Nvidia Go or similar integrated chipset.

---

### Post by zyth on 2007-08-24
It won't matter, I've backported Mesa 7.01 to Feisty and rebuilt Xorg from the sources in Gutsy as well, and the issue still occurs.  It seems to be related to Wine and/or WoW itself.  You *can* run WoW in wine in Direct3D mode, but it runs incredibly badly - something like 5-7fps outdoors, and 14-16 indoors, as well as having odd graphical issues.

---

### Post by cogadh on 2007-08-24
I would suggest that since so many other people can run WoW with no issues on different hardware, that the problem does not lie with Wine or WoW, but comes back to (once again) the Intel driver just not being good enough to do what WoW needs.

---

### Post by eggplant37 on 2007-08-24
> **hikaricore said:**
> The intel chipset is integrated into the motherboard.  If this is a desktop system then you're best going with a PCIe or AGP Nvidia card.  If this is a laptop, you'd have to get an entirely new one with an Nvidia Go or similar integrated chipset.

Thank you, Captain Obvious! You're my hero. Yes, it's a laptop. Yes, unless I contact Dell and exchange machines, I guess I'm to be buggered with naught but the likes of the "Get a better video card" set.

You see, to me, that's copping out. The hardware I bought is just as capable as the Nvidia and ATI-equipped machines at handling the graphics, just not as pretty and not as quickly. I'd be happier with a post that might tell me how to approach finding a solution to my problem or new things to try. Anyone else got any ideas?

---

### Post by cogadh on 2007-08-24
You really don't get it do you? Your card may be capable in Windows (which is debatable), but it is not in Linux. The driver support for Intel chipsets is not the greatest in Linux, especially when compared to the kind of driver support you get with an Nvidia product. It is not a cop out, it is a fact that there is likely nothing you can do to fix the problem, other than replace that Intel chipset with an Nvidia one. 

If you expect to get help on these boards, I would suggest that you try to be a little less rude when someone presents with a suggestion that is a viable solution, even if it is something that you didn't want to hear.

---

### Post by eggplant37 on 2007-08-24
> **cogadh said:**
> You really don't get it do you? Your card may be capable in Windows (which is debatable), but it is not in Linux. The driver support for Intel chipsets is not the greatest in Linux, especially when compared to the kind of driver support you get with an Nvidia product. It is not a cop out, it is a fact that there is likely nothing you can do to fix the problem, other than replace that Intel chipset with an Nvidia one. 

If you expect to get help on these boards, I would suggest that you try to be a little less rude when someone presents with a suggestion that is a viable solution, even if it is something that you didn't want to hear.

No, trust me, I'm getting it RIGHT NOW, yet another post from someone whose only response is, "Dude, get another card!" Nope. Next answer, please. There has to be someone who's managed to get farther than I have on this same chipset, and I'll hold the conversation open until that person shows up.

As to attitude, there has to be more than, "Dude, get another card!"

Thanks for playing, though; your response is rather entertaining.

---

### Post by hikaricore on 2007-08-24
Hundreds have come before you with similar Intel chipsets, very few have walked away successful.
Simply because you expect something to work better than it does, doesn't mean it's going to happen.

If you want help be nice and people on these forums will do their best.  We are not paid to help you, we volunteer our time.
Take your past software tech support bitch/whine attitude and stuff it, because it's not going to get attention here.

---

### Post by eggplant37 on 2007-08-24
> **hikaricore said:**
> Hundreds have come before you with similar Intel chipsets, very few have walked away successful.
Simply because you expect something to work better than it does, doesn't mean it's going to happen.

If you want help be nice and people on these forums will do their best.  We are not paid to help you, we volunteer our time.
Take your past software tech support bitch/whine attitude and stuff it, because it's not going to get attention here.


Great answer! Let's give up before we even try, especially when given a newer chipset that could work better if someone paid attention to the problem rather than giving the stock response.

Yes, I understand the volunteer concept behind free software. I've run linux since 1997. I'm simply looking for a better answer than, "Dude, buy another card!" Maybe someone else would like to play?

---

### Post by hikaricore on 2007-08-24
> **eggplant37 said:**
> Great answer! Let's give up before we even try.

Works for me, best of luck to ya.

---

### Post by zyth on 2007-08-24
Actually, the Intel GPU works fine for most Linux-native games.  So 'get another GPU is kind of an odd comment.  Also, I found some ways to (possibly) increase the FPS in D3D mode for WoW in Wine, I'm going to try it out when I get home tonight.  If I get a (playable) framerate, I'll post a comment.  So far 5-7fps outside and 13-16fps inside isn't cutting it.

---

### Post by eggplant37 on 2007-08-24
> **zyth said:**
> Actually, the Intel GPU works fine for most Linux-native games.  So 'get another GPU is kind of an odd comment.  Also, I found some ways to (possibly) increase the FPS in D3D mode for WoW in Wine, I'm going to try it out when I get home tonight.  If I get a (playable) framerate, I'll post a comment.  So far 5-7fps outside and 13-16fps inside isn't cutting it.

Care to share your xorg.conf with me, please?

---

### Post by zyth on 2007-08-24
Sure, I can share what I have right now, but I have not been home to test the changes for FPS-ish stuff yet, so this may seriously break X (I am ssh'd in to my box from work right now). 
> 
Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
        Load    "dbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        VideoRam        131072
        Option          "AGPMode" "4"
        Option          "AGPFastWrite"  "true"
        Option          "EnablePageFlip" "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection


---

### Post by eggplant37 on 2007-08-24
> **zyth said:**
> Sure, I can share what I have right now, but I have not been home to test the changes for FPS-ish stuff yet, so this may seriously break X (I am ssh'd in to my box from work right now).

Yep, understandable. I'm at home, full access including remote ssh in case X freezes. I'll play with your xorg.conf and see what changes in my situation. Thanks for dropping that off.

---

### Post by zyth on 2007-08-24
Okay, if you can let me know how it works?  Thanks!

---

### Post by eggplant37 on 2007-08-24
> **zyth said:**
> Okay, if you can let me know how it works?  Thanks!

Not too much different, but now it's looking more and more like a wine issue. I'm running stock 0.9.43 right out of the Feisty repositories, and I've another copy of 0.9.41 custom-rolled and installed that crashes worse.

At least I'm getting closer to where the problem may be. 

/usr/bin/wine ./WoW.exe -opengl
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreatePbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleasePbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyPbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryPbufferARB) - not found
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f520,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
Segmentation fault (core dumped)

Cedega is even worse; just a black screen with a mouse cursor, and X just freezes the machine. Took a ssh login to reboot gracefully.

---

### Post by zyth on 2007-08-24
Ohh, no, don't use -opengl, use -d3d.  -opengl is broken by WoW/wine and some interaction thereof.

---

### Post by eggplant37 on 2007-08-24
> **zyth said:**
> Ohh, no, don't use -opengl, use -d3d.  -opengl is broken by WoW/wine and some interaction thereof.

Heh. Not much better

/usr/bin/wine ./WoW.exe -d3d
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreatePbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleasePbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyPbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryPbufferARB) - not found
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreatePbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleasePbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyPbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryPbufferARB) - not found
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x176f88) : stub, simulating 64MB for now, returning 64MB left
Segmentation fault (core dumped)

---

### Post by zyth on 2007-08-24
Very odd, I don't have that occur when I run WoW.... when I get home I will check my config and such and post it on here.  I know I am using 0.9.43 wine, and such.  One thing, you need to have wine set to Windows XP, and sound to OSS.  Also, you have to have already watched the opening movie, or set your Config.wtf to bypass it.

---

### Post by eggplant37 on 2007-08-24
> **zyth said:**
> Very odd, I don't have that occur when I run WoW.... when I get home I will check my config and such and post it on here.  I know I am using 0.9.43 wine, and such.  One thing, you need to have wine set to Windows XP, and sound to OSS.  Also, you have to have already watched the opening movie, or set your Config.wtf to bypass it.

Nope, no diff. Let me know what you find, and thanks for your input.

---

### Post by Seraed on 2007-08-25
> **zyth said:**
> Very odd, I don't have that occur when I run WoW.... when I get home I will check my config and such and post it on here.  I know I am using 0.9.43 wine, and such.  One thing, you need to have wine set to Windows XP, and sound to OSS.  Also, you have to have already watched the opening movie, or set your Config.wtf to bypass it.

Alsa works fine for me. Not even using Aoss.

> 
Ohh, no, don't use -opengl, use -d3d. -opengl is broken by WoW/wine and some interaction thereof.
There does not seem to be any issue with OGL except the patch process which is easily solved by turning off OGL just for the patch.

---

### Post by zyth on 2007-08-25
And you have Intel graphics?

---

### Post by eggplant37 on 2007-08-25
> **zyth said:**
> And you have Intel graphics?

Specifically, the 965GM chipset here.

---

### Post by zyth on 2007-08-25
Okay, so it works, and is mostly playable except for drops to 8fps or so in Orgrimmar for me... xconfig is as you had.  Here is my Config.wtf:
> 
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxWindow "1"
SET hwDetect "0"
SET movie "0"
SET readTOS "1"
SET realmList "us.logon.worldofwarcraft.com"
SET gxMultisampleQuality "0.000000"
SET readEULA "1"
SET readScanning "-1"
SET realmName "Shadow Council"
SET gameTip "61"
SET SmallCull "0.070000"
SET farclip "177"
SET MusicVolume "0.60000002384186"
SET SoundVolume "1"
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET MasterVolume "1"
SET ffx "0"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET mouseSpeed "1"
SET cameraPitchMoveSpeed "90"
SET cameraYawMoveSpeed "180"
SET cameraPitchSmoothSpeed "45"
SET cameraYawSmoothSpeed "180"
SET cameraSmoothStyle "0"
SET cameraSmoothTrackingStyle "0"
SET cameraDistanceMaxFactor "1"
SET SoundZoneMusicNoDelay "1"
SET gxColorBits "24"
SET gxApi "d3d"
SET statusBarText "1"
SET ffxDeath "0"
SET ffxGlow "0"
SET minimapZoom "0"
SET guildMemberNotify "1"
SET profanityFilter "0"
SET readContest "-1"
SET minimapInsideZoom "5"
SET gxDepthBits "24"
SET locale "enUS"
SET gxTripleBuffer "1"
SET lod "1"
SET baseMip "1"
SET spellEffectLevel "0"
SET expansionMovie "0"
SET Gamma "1.000000"
SET lastCharacterIndex "2"
SET showToolsUI "1"
SET patchlist "us.version.worldofwarcraft.com"
SET weatherDensity "0"


---

### Post by eggplant37 on 2007-08-25
> **zyth said:**
> Okay, so it works, and is mostly playable except for drops to 8fps or so in Orgrimmar for me... xconfig is as you had.  Here is my Config.wtf:

I've about 15 minutes to work here and will test it after I'm finished. I'll let you know what I find here.

I noted that Wine updated to 0.9.44 sometime yesterday. I may even give that a shot.

---

### Post by eggplant37 on 2007-08-25
> **zyth said:**
> Okay, so it works, and is mostly playable except for drops to 8fps or so in Orgrimmar for me... xconfig is as you had.  Here is my Config.wtf:

Okay, here's my wine output:

/usr/bin/wine ./WoW.exe -d3d
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreatePbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleasePbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyPbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryPbufferARB) - not found
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f584,0x00000000), stub!
err:wgl:X11DRV_wglGetProcAddress (wglMakeContextCurrentARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetCurrentReadDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglCreatePbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglGetPbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleasePbufferDCARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDestroyPbufferARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglQueryPbufferARB) - not found
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x176fd8) : stub, simulating 64MB for now, returning 64MB left
Segmentation fault (core dumped)


Gonna check it with Cedega and see what it does.

---

### Post by eggplant37 on 2007-08-25
> **eggplant37 said:**
> 


Gonna check it with Cedega and see what it does.

Yep, just as bad. The WoW directory copy from my XP drive generates an WoW error under Cedega, and the error message does get sent to Blizz.

Another install done straight off the install CDs under Cedega last weekend hangs X with a black screen and necessitates a remote login and gdm restart.

I'm getting to the point where I may as well just surrender to using the XP installation on my other laptop for my gaming since one or both of the Intel drivers or Wine aren't stable enough to deal or something is missing from the equation that I've not found yet. I'll watch this thread and see what others have to offer as fixes.  If anyone else wants to help and needs to see anything, let me know.

My goal is to get as free of Uncle Bill's monstrosity as I can. I'm able to run XP in VMWare, since I work in medical transcription for a living and depend upon a MS Word overlay program to process the jobs. Up until I got back into medical transcription 2 years ago, I had been free of Windows entirely since about 2000 or so.

---

### Post by zyth on 2007-08-25
If you pop on #ubuntuforums on freenode, maybe I can try and help you sort out what the difference is between my setup and yours.  Its a bit difficult to do on here.  If not, good luck with the quest to get WoW running I spose. :)

---

### Post by eggplant37 on 2007-08-25
> **zyth said:**
> If you pop on #ubuntuforums on freenode, maybe I can try and help you sort out what the difference is between my setup and yours.  Its a bit difficult to do on here.  If not, good luck with the quest to get WoW running I spose. :)

Ya did a fine job of helping me along with getting my config. I may have this licked before midnight local, which is still 4+ hours away. I'll let ya know where it stands. 

Right now, top indicates that when I invoke WoW under Wine, my cpus peg, hitting 100% and sometimes 101% (these go to 11.)

More digging.

---

### Post by eggplant37 on 2007-08-25
> **eggplant37 said:**
> Ya did a fine job of helping me along with getting my config. I may have this licked before midnight local, which is still 4+ hours away. I'll let ya know where it stands. 

Right now, top indicates that when I invoke WoW under Wine, my cpus peg, hitting 100% and sometimes 101% (these go to 11.)

More digging.

Further progress. Using aoss to wrapper wine gets sound out in the form of the music that plays at the login screen. Now if only I could get a picture!

Last set of wine message that prints before I kill -9 the process from a remote ssh login is at:  

[http://pastebin.com/d62ce5dc4](http://pastebin.com/d62ce5dc4)

---

### Post by zyth on 2007-08-26
The problem is WIne 0.9.44, I downgraded to 0.9.39, got in.  I imagine 0.9.43 would work too, as it was for me previously, but after 0.9.44 I had the same issue.

---

### Post by starcannon on 2007-08-26
Cogadh I agree on most of your points, and indeed I wanted the nvidia chipset with my 1420n, however Dell did not offer it when I ordered mine and last I looked they still don't... unless I order a 1420n with MS windows on it, I sadly ordered the Ubuntu version and was assured by the sales person (even made him go check it out) that my 3D applications would run just fine. He was *mostly* right, for instance Beryl runs like a champ, as does Google Earth etc... Cedega/Wine neither are happy. The true oddity here is that Intel offers a Free(liberated) driver, while ATi and Nvidia are Closed, yet the Free driver is utter shite in comparison. Another unfortunate reality is I am only a power-user/lamer, I can not really help develop the drivers... though in a few years who knows(I'm just 1 year away from entering Comp Sci program at EWU) Anyway until I have the mental resources to help build/fix these issues I am at the mercy of the available developement community; who, I have noticed in our beloved linux forums are very fast to deride closed source, and yet while deriding that, do not even come close to performing as well when given the opportunity like intel has offered. 

Okay, Okay /rant off, to make my position clear though let me recap.
I am a bit frustrated that Dell assured me 3D was just fine when in fact its not, I am a little taken back that an open driver with support from the vendor is not nearly as good as the closed drivers from ATi and Nvidia. And no confrontation meant, but I'm having a hard time understanding why the common answer in the forums is to scrap a lap-top and get another with Nvidia on it when there is a perfectly fine open chipset in the one I have (and its brand new, $1500 with the option upgrades I chose, and Nvidia wasn't in the offering else I surely would have chosen it)  The real answer for this I guess, is patience and hope that given 6~18 months a great driver for the intel'd 1420n's will emerge... or in our case apt-get :)

Thanks for listening to my rant. 
~Starcannon

---

### Post by zyth on 2007-08-26
I am not sure that the fault is in the Intel drivers, as Linux native apps run fine - it seems to be a bug in Wine of some sort, or in Wine+WoW in this case... I am not entirely sure.  Maybe I will install Guildwars tonight to see how that runs in Wine so I can see if its Wine itself, or just Wine+WoW.

---

### Post by cogadh on 2007-08-26
You cannot judge the performance of games run through Wine based on the performance of native games, they are completely different animals. Native games don't have to deal with a compatibility layer translating DirectX calls into the closest native counterpart, like games through Wine do. 

You are also forgetting one other possibility: it is a problem with Wine and the Intel driver. Since so many people are already able to play WoW using Wine with the Nvidia and ATI drivers, one can logically deduce that there is the *possibility* of a problem/conflict with the Intel driver. It is entirely possible that Wine is trying to take some call from Direct3D and translate it into its OpenGL counterpart, which may not be supported by the Intel driver. That could certainly explain the radical difference between the performance achieved on an ATI or Nvidia system as opposed to the Intel system. It would also explain why the game would perform just as poorly if run in OpenGL mode instead of Direct3D.

It should be noted, however, that there appears, based on the forum posts here and elsewhere, to be a significant bug between the most recent patch for WoW and Wine, possibly only with the latest version of Wine (0.9.44). Until that is resolved/confirmed, I don't think anyone can really determine where the true problem lies.

---

### Post by zyth on 2007-08-26
Well, the problems occur in 0.9.43 as well, so I am expecting it is quite possibly some incompatibility in Wine and the Intel driver as you have suggested, but I havent' tried any games in Wine but WoW yet, so I am unsure.  I am going to install Guild Wars tonight and see if there are similar issues.  That should help narrow it down.

---

### Post by eggplant37 on 2007-08-27
> **cogadh said:**
> It should be noted, however, that there appears, based on the forum posts here and elsewhere, to be a significant bug between the most recent patch for WoW and Wine, possibly only with the latest version of Wine (0.9.44). Until that is resolved/confirmed, I don't think anyone can really determine where the true problem lies.

I agree with this statement wholeheartedly. I've futzed about with several versions of Wine, the intel driver, mesa GL, and the latest Cedega with the Intel G965 chip, all with the same result: I get audio out of Warcraft, but no video, and within seconds of starting wine with WoW, CPU usage spikes to 100% on both cores, resulting in the GUI becoming inoperable until WoW.exe is killed from a remote ssh session.

Looks like it's going to be slow going, though I do wonder whether or not the intel driver devel team or the Wine devel team would welcome some additional input? How do I proceed? I'm no developer either; however, I think that I certainly could help in the debugging process.

---

### Post by radcc07 on 2007-09-04
I don't believe it's an issue with the Intel drivers.  I have a laptop with an ATI Radeon 9600 (32MB) and I have the same issue shown a the start of this thread when using the latest Cedega package to run World of Warcraft.

_ I have to retrack my statement.  I pulled a really really noob move. I am able to play at this time with the latest Cedega.  Sorry.

---

### Post by ImNeat on 2007-09-15
Any more progress on this issue?  I can't boot into WoW on my 1420N - a segfault kills the process.  New version of wine released today (0.9.45) but still same problem =(.

Output:
```
fixme:advapi:SetSecurityInfo stub
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:win:EnumDisplayDevicesW ((null),0,0x33edac,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33ecd4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f2d0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5b0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5a8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f530,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f520,0x00000000), stub!
fixme:system:SystemParametersInfoW  Unimplemented action: 113 (SPI_SETMOUSESPEED)
Segmentation fault (core dumped)
```

also, I had to manually create a Config.wtf because I haven't even gotten close to being able to log in a toon yet.

---

