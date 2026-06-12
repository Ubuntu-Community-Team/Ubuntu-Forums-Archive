---
title: "WoW unable to start 3d acceleration"
date: 2007-03-18
forum: Gaming &amp; Leisure
---

### Post by Tellisk on 2007-03-18
Installed WoW and TBC. Downloaded video driver from Synaptic.

In terminal, when I type
```
wine WoW.exe -opengl
```

i get

```
err:secur32:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7dc10000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7dc10000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33ede4,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f34c,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f5ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f554,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f540,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x23), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x23), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x23!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f554,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f540,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x23), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x23!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f554,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f540,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x23), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x23!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f554,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f540,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x23), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x23!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f554,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f540,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x23), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x23!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f554,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f540,0x00000000), stub!
fixme:xrandr:X11DRV_XRandR_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wgl:get_fbconfig_from_visualid No fbconfig found for Wine's main visual (0x23), expect problems!
err:wgl:init_formats Can't get the FBCONFIG_ID for the main visual, expect problems!
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 1
err:wgl:X11DRV_ChoosePixelFormat Can't find a matching FBCONFIG_ID for VISUAL_ID 0x23!

```

followed by a pop-up "WoW is unable to start 3d acceleration"

AMD Athlon XP 2g (pretty sure)
ATI Radeon 9800 (i know they commonly have problems)
Edgy 6.10

Any help is most appreciated =)


RESOLVED: the program Envy solved my problem. very painless, indeed!

---

### Post by Death_Sargent on 2007-03-18
First of all i recomend playing this game under cedega because it really does work well without a hitch under it. 

TWO, the fact is your using a DirectX emulator to do opengl functions which causes errors and in the end your not going to get a boost in frame rate that is worth mentioning. 

if you really want the two extra frames persecond then I recomend trying this trick under cedega because i know it works with their wine configs.

Also its likely the driver you have or your video card does not actually support full opengl acelleration.

One final note. If you have beryl compiz, compositmanager. or even just an xgl desktop you are going to have problems running opengl games period.

If none of that applies then atleast this post will keep the thread alive. hopefully so you can get some real tech support. 

Word to the wise try disabling any special desktop opengl effects and then installing proprietary drivers.

---

### Post by Death_Sargent on 2007-03-18
**I forgot ATI DOES NOT DO FULL OPENGL ACCELLERATION**

Fact is the ATI drivers are not there yet. its on the site if you don't beleave me. until ATI or mesa figures out all of the opengl problems your gona have to deal with a slightly lessened frame rate. 

I use an ati 9700 radeon. we are on the same driver so just trust me on this. it should not work at all

Stick to the DirectX emulation way of playing

---

### Post by hikaricore on 2007-03-19
> **Death_Sargent said:**
> First of all i recomend playing this game under cedega because it really does work well without a hitch under it.

Worst advice ever.

---

### Post by Tellisk on 2007-03-19
Okay, so now I have another problem. I may need to start a new thread as the title of this one may not draw in the right people who can help, but we'll see (don't want to clog the forum with my bs)

I started playing, and was happy to get it working. Not 100% satisfied, but happy. Movement/spellcasting is very choppy. I foresee myself trying to run an instance or PVP like this and I would be useless in either. 

I'd already done the regedit tweak from the wiki, so I went on to try tweak #2. The one that had me write a script to launch WoW on a dedicated X server. Tried it twice, and found that when I type the command ```
./launch.sh
```
as prompted in step 5 on the wiki, the screen goes black, and there is no way out (short of the Reset button on the tower).

Is there another way to get my graphics smoother? or a way to edit this tweak to make it work for me? Would I be better off snagging an nVidia card, since it seems much more compatible with Linux?

Thanks in advance.

---

### Post by hikaricore on 2007-03-19
**I'm about to spout a bunch of info about switching between virtual screens in linux, this may be of benefit for you to know.**


In linux you can switch between "screens" by hitting ctrl+alt+F# depending on which screen you want.

In ubuntu by default your regular desktop is on: ctrl+alt+f7

The dedicated X server for your game via that script should be on: ctrl+alt+f9

You can also reach text terminals at anytime by using: ctrl+alt+f1, ctrl+alt+f2, ctrl+alt+f3, ctrl+alt+f4, ctrl+alt+f5, or ctrl+alt+f6

Knowing this should reduce the number of uses that need to be made of the Power/Reset Buttons.

As far as making it work better?  Close any open programs you don't need, end any services you're not using, ect.  Example: if you're running a bunch of torrents and a paused video in the background it's not going to help your framerate in the least.

But for the most part I can safely say you may be better off with an Nvidia card.

Good Luck,

--Aaron

---

### Post by Tellisk on 2007-03-19
Wow, thanks. I had no idea about that ctrl alt F function.

I'll shop around online for a good card tomorrow. Can you recommend one perhaps? I'd like to not spend much more than 100 bucks if that is possible. Of course, I don't want to sell myself short (for gaming, watching movies, etc), so if I need to, I can afford to go a bit higher.

---

### Post by Tellisk on 2007-03-19
Well, er... no. =(

I tried launching again using that command. Black screen, but this time thought I'd be okay with this new trick in my arsenal.

Unfortunately, Ctrl Alt F1-F9 seem to have done nothing for me at this point and I was reduced to the only trick I have left: Hitting my PC with an aluminum baseball bat.

I kid. Just had to Reset again =(

I'll play with it more tomorrow in between shopping for that new card. G'night.

---

### Post by Praill on 2007-03-19
I run WoW as follows and get drastic improvements to my fps:
WINEDEBUG="fixme-all" wine WoW.exe -opengl

Also, if youre using an ATI card do you have this section appended to your xorg.conf file?
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
Apparently the newest verisons of xorg enable Composite extension by default, which dont work in the ATI driver yet.

I also had to add the following 3 lines to the device section of my xorg.conf to get the game to play without crashing. Maybe it will help fps too, i dont know.
Option	    "Capabilities" "0x00000800"
Option	    "UseFastTLS" "off"
Option	    "KernelModuleParm" "locked-userpages=0"

This is all I can think of to help. WoW still doesnt run as well for me as it does in winblows, but I blame this entirely on the shitty linux ATI drivers. If youre shopping for a new card pick up nVidia for sure.

Oh, and dont use cedega. Cedega sucks. Even if cedega could out-perform wine for wow (which it cant) your problem seems to be hardware related, not really wine related.

---

### Post by lakersforce on 2007-03-19
> **hikaricore said:**
> 
>  Originally Posted by Death_Sargent  View Post
First of all i recomend playing this game under cedega because it really does work well without a hitch under it.

Worst advice ever.

I second that.

---

### Post by Tellisk on 2007-03-19
> **Praill said:**
> I run WoW as follows and get drastic improvements to my fps:
WINEDEBUG="fixme-all" wine WoW.exe -opengl

Also, if youre using an ATI card do you have this section appended to your xorg.conf file?
Section "Extensions"
	Option	    "Composite" "Disable"
EndSection
Apparently the newest verisons of xorg enable Composite extension by default, which dont work in the ATI driver yet.

I also had to add the following 3 lines to the device section of my xorg.conf to get the game to play without crashing. Maybe it will help fps too, i dont know.
Option	    "Capabilities" "0x00000800"
Option	    "UseFastTLS" "off"
Option	    "KernelModuleParm" "locked-userpages=0"

This is all I can think of to help. WoW still doesnt run as well for me as it does in winblows, but I blame this entirely on the shitty linux ATI drivers. If youre shopping for a new card pick up nVidia for sure.

Oh, and dont use cedega. Cedega sucks. Even if cedega could out-perform wine for wow (which it cant) your problem seems to be hardware related, not really wine related.

```
WINEDEBUG="fixme-all" wine WoW.exe -opengl
```
didn't work for me, I was getting like 3 fps at best. The "Extensions" section is already in my xorg.conf file, but regarding the "Device" section, I have two. Does it matter which I put those 3 "Options" under?

```
Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

```

is what I currently have. Thanks.
Also, what should I look for in a video card if I choose to buy an nvidia?

Edit: This looks good for the money, any feedback?
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2746206&Tab=2&NoMapp=0](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2746206&Tab=2&NoMapp=0)

---

### Post by sdman on 2007-03-21
Alright so I am getting the same error as Tellisk. I have a GeForce 7600gt ..Im assuming that I have to get updated drivers from nvidia? Though I thought the driver in my sig was the most recent one I could have. Apparently not.. Any suggestions? Btw tess I usually shop newegg because of the amount of reviews it has to offer for components [ BIOSTAR V6802XA21 GeForce 6800XT]("http://www.newegg.com/Product/Product.asp?Item=N82E16814141038") I think there are better cards for the same price range. Mine is a evga.

---

### Post by Tellisk on 2007-03-22
> **sdman said:**
> Alright so I am getting the same error as Tellisk. I have a GeForce 7600gt ..Im assuming that I have to get updated drivers from nvidia? Though I thought the driver in my sig was the most recent one I could have. Apparently not.. Any suggestions? Btw tess I usually shop newegg because of the amount of reviews it has to offer for components [ BIOSTAR V6802XA21 GeForce 6800XT]("http://www.newegg.com/Product/Product.asp?Item=N82E16814141038") I think there are better cards for the same price range. Mine is a evga.

I dunno if this'll help you, but have you tried tseliot's program for acquiring the correct driver? If you don't have the right one, it ought to get you there.

---

### Post by Scotty562 on 2007-03-24
Did this problem ever get solved?

---

### Post by lakersforce on 2007-03-24
Did you edit the WTF\Config.wtf file in your WoW install directory:

```
SET gxApi "OpenGL"
```

---

### Post by Scotty562 on 2007-03-24
Yes.

---

### Post by gigermunit on 2007-03-24
I got it to run with everything working on d3d but it freezes when i start world and character modeling but in opengl it's freezy the entire time.

---

### Post by hikaricore on 2007-03-24
> **gigermunit said:**
> I got it to run with everything working on d3d but it freezes when i start world and character modeling but in opengl it's freezy the entire time.


It's been doing that for alot of people in d3d mode past 0.9.25 or so, no one's really
pinpointed the cause of this yet.  Mine does the exact same thing in d3d, crashes on
zone in.

---

### Post by Praill on 2007-05-07
Putting these 3 lines:
Option "Capabilities" "0x00000800"
Option "UseFastTLS" "off"
Option "KernelModuleParm" "locked-userpages=0"
in the device section fixed the freezing on login problem for me.

You put them in the section labeled: aticonfig-Device[0]
Default Screen is probably not being used by X anymore if you have direct rendering.


Sorry its taken me so long to repsond. I started a new job, been doing some side projects, etc, etc, poor me :)

I hope youre still watching this thread.

---

### Post by Tellisk on 2007-05-07
I hate to bump such an old thread, but now that I've upgraded to Feisty, I'm having some problems.

Trying to start WoW in openGL gives me the old "World of Warcraft is unable to start 3d acceleration."

And in d3d I can't get past the login screen because my cursor stays the default arrow and the gauntlet cursor does not move when I move the mouse, also I don't expect that even if I could get past that in d3d, I would be able to play, because the login screen music and graphics are the choppiest thing I have ever seen.

Anyway, I can't get 3d acceleration to start in opengl, and have been going on the assumption that it's my driver, which, try as I may, does not install without giving me an error. I have tried both in a terminal with sudo aptitude install nvidia-glx-new and in the Restricted Drivers Manager.

I'm wishing I hadn't upgraded, but going back would be such a pain with having to reinstall and reconfigure everything all over again. I just wish I could get my video driver working. Thanks in advance.

---

### Post by RobinOfSweden on 2007-05-08
Tellisk are you using a 64bit or 32bit system? in 64bit Feisty Wine _can_ have troubles with locating my graphic cards driver/OpenGL thingies (I used the CrossOver from wineHQ to get a more sensible error message and it returned it with my graphic card lacking 3D support or if it was 3D acceleration support which it does... do'h. Which ended with me going down to a 32bit Feisty instead and it works perfectly here without any special thingies needing to be done).

Also have you added the Multiverse and Universe in your repositery? when you use apt-get / synaptic it makes it possible to get the latest drivers and latest version of some programs (if i understood it correctly). For me in both 32bit and 64bit tsElliot's Envy script for installing graphic drivers worked like a charm each time but i have heard some people have had problems with it.

Hope it helps!

---

### Post by Praill on 2007-05-08
> **Tellisk said:**
> I hate to bump such an old thread, but now that I've upgraded to Feisty, I'm having some problems.

Trying to start WoW in openGL gives me the old "World of Warcraft is unable to start 3d acceleration."

And in d3d I can't get past the login screen because my cursor stays the default arrow and the gauntlet cursor does not move when I move the mouse, also I don't expect that even if I could get past that in d3d, I would be able to play, because the login screen music and graphics are the choppiest thing I have ever seen.

Anyway, I can't get 3d acceleration to start in opengl, and have been going on the assumption that it's my driver, which, try as I may, does not install without giving me an error. I have tried both in a terminal with sudo aptitude install nvidia-glx-new and in the Restricted Drivers Manager.

I'm wishing I hadn't upgraded, but going back would be such a pain with having to reinstall and reconfigure everything all over again. I just wish I could get my video driver working. Thanks in advance.

Most likely a video driver thing. I recently discovered a program called Envy that works wonders installing drivers. Im at work so i cant give a link, but it shouldnt be hard to find.

---

### Post by Tellisk on 2007-05-08
I could have sworn I made a reply to this this morning from my girlfriend's... oh well.

I discovered from my post in the Multimedia & Video section that the new Unstable version of Envy works with Feisty, which I hadn't realized was released. I tried it and it didn't work for me. 

It's a 32 bit system and multi/universe repos are enabled.

[http://ubuntuforums.org/showthread.php?t=436240](http://ubuntuforums.org/showthread.php?t=436240) is the other thread which has my error messages in detail, if anyone here thinks (s)he may be able to help. 

Basically running Envy, I get an error that the package nvidia-kernel-source could not be built successfully. It then goes through the rest of the process followed by reconfiguring xorg.conf and offering me the option to reboot. After all that, it seems nothing is different. The button for nVidia Settings appears in my Applications -> System Tools menu, but when I click it, I get the error that the target process does not exist. 

I appreciate the replies here, I'm getting rather frustrated with the whole thing.

---

### Post by Tellisk on 2007-05-09
I think the only thing I can do now is to use my good old 6.10 cd and start from scratch. It's going to be a pain, but so is trying to make this square peg fir in the round hole. Thanks for the help. If you think of anything, let me know because I'm giving it a little while before I go through with this decision.

---

### Post by Jaza on 2007-05-09
```
Section "Device"
        Identifier  "ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
        Driver      "ati"
        BusID       "PCI:1:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

```

You have 2 displays in use ?
You could change that upper device with same driver and options as the lower one (if it happens to be your primary desktop).

---

### Post by GIBson3 on 2007-05-09
I'm not sure this is of any help... but I'm in 7.04 (Xubuntu) and built Wine v0.9.36.  WoW's not overly playable on a 1.0gig p3 w/ 1 gig of ram and a GF3... but it's working all right all things considered(10-15 fps in Ironforge).


**<<xorg.conf>>**
```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "DELL  M991"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce3"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "CRT: 1600x1200_60 +0+0; CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

**<<config.wtf>>**
```

SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET doodadAnim "0"
SET lodDist "100.000000"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "32"
SET farclip "477"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET SoundOutputSystem "1"
SET gxResolution "1600x1200"
SET movie "0"
SET gxApi "OpenGL"
SET gxWindow "1"
SET readTOS "1"
SET readEULA "1"
SET readScanning "-1"
SET readContest "-1"
SET gxCursor "0"
SET shadowLevel "0"
SET anisotropic "16"
SET DesktopGamma "1"
SET Gamma "1.000000"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "1"
SET realmList "us.logon.worldofwarcraft.com"
SET ffxGlow "0"
SET ffxDeath "0"
SET gameTip "22"
SET AmbienceVolume "0.60000002384186"
SET uiScale "1"
SET specular "1"
SET mouseSpeed "1"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraWaterCollision "0"
SET cameraDistanceMaxFactor "1"
SET statusBarText "1"
SET SoundZoneMusicNoDelay "1"
SET locale "enUS"
SET expansionMovie "0"
SET lastCharacterIndex "8"

```
(note: I removed the Account name from the above .wtf)

---

### Post by ImNeat on 2007-05-26
For me this issue was happening because my restricted ATI driver wasn't actually in use.  Check System -> Admin -> Restricted Drivers Manager to see if you have a restricted driver and to see if it's in use.


*Note - sorry if this has already been suggested or isn't exactly relevant to your case.  I'm only posting because I just spent about an hour on this and finally found a fix so I figured I'd share in the most recent and relevant thread.  I hope it helps.

---

### Post by ShadowFlar3 on 2007-05-27
Allright I'll give my 2 cents since I've battled with ATI drivers so much myself.

Firstly, make sure your ATI drivers are correctly installed by doing:

glxinfo | grep rendering

If you get Direct rendering: yes, your drivers are good and the problem is caused by something else. Check and re-check your config.wtf for

SET hwDetect "0" (prevents WoW from autodetecting your settings and setting d3d rendering for example)
SET gxColorBits "24" (same as desktop)
SET gxDepthBits "24" (same as desktop
SET gxRefresh "60" (same as desktop)
SET gxApi "OpenGL"
SET gxResolution "1280x1024" (same as desktop)

If you get no you need to fix the driver install. I strongly suggest using package manager like synaptica for everything because of the ease and stability allthough they won't most likely be the newest drivers available. There are plenty of how-tos on that subject elsewhere but if something's unclear you can PM me or ask in this thread about it.

---

