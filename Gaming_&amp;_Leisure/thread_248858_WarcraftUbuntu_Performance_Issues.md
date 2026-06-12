---
title: "Warcraft/Ubuntu Performance Issues"
date: 2006-09-01
forum: Gaming &amp; Leisure
---

### Post by MattKemp on 2006-09-01
I'm playing World of Warcraft on Linux at the moment and i'm encountering some serious performance issues with it.

This PC is relatively high spec (Ath. 64 3800, 7300GS, 1GB DDR400) yet I get around 4-8 FPS whereas I used to get 30-40 in windows, on a lower spec machine with high settings on. I'm running at low settings at the moment.

I have a feeling that it's a memory problem as it's pretty much constantly stacked to full, but swap space is never used. Unless I'm misunderstanding something, my machine should use swap space as 'virtual' memory?

I'm a little miffed as to why a less bloaty OS should achieve such poor results. I understand that there's an overhead with Wine, but 7 FPS on all-low settings?

-Confused midget.

---

### Post by SavageBeginner on 2006-09-01
Have you installed the Nvidia driver?  Without it you will not get very good 3D performance.

Here's a how to install it:  [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by MattKemp on 2006-09-01
Yeah, I've got the nvidia driver in and it's specified in my xorg.conf - I do have twinview running, but I don't see how that could adversely affect my framerate that badly.

---

### Post by palmargard on 2006-09-01
try running:

```
glxgears -printfps
```

in terminal, and check the results. with a half-decent 3d cart you should be getting at least couple of thousands fps (I'm getting 13k fps with my Ati x700 card, and ati linux drivers aren't the best around).

If you're getting low fps you need to configure your video card settings, very probably something in the xorg file. If you get good results from glxgears the problem is probably wine/wow based.

---

### Post by ugli on 2006-09-02
Are you using the -opengl parameter for wow?

```
wine wow.exe -opengl
```

---

### Post by Holmgreen on 2006-09-02
I have the exact same problem.
I get around 1100 fps on the gear-test, and i do use the -opengl command to start WoW.

I'm playing through Cedega though, but always with a framerate below 10fps (was on a 20 man raid yesterday, with a constant framerate on 4-6fps - not good for a healer ;) )

Playing with a Nvidia FX 5200 btw.

This is how my xorg.conf looks like:

---------------------------------------
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "dk"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
------------------------------------------

I guess i have my Nvidia configured alright. So.... do any of you think it would be better for me to play through Wine? Would it improve performance?

/Holmgreen

---

### Post by thieves.honor on 2006-09-02
I have the same problem with my laptop.  Runnig windows I get around 20-25fps, but in linux I get around 5-10fps.  I have a ATI X300 with the ATI driver installed.  running glxgears -printfps produces around 2000fps.  I installed using wine following the directions from the winehq site for appling the WoW patches.

---

### Post by Holmgreen on 2006-09-02
Oh... just one more question:

If i like to try playing WoW through Wine instead of Cedega - do i really have to reinstall the entire game? Is there some way to use the same installation as Cedega are using?

---

### Post by eqisow on 2006-09-02
Holmgreen, yes there is.

Since you already have it installed in Cedega, you can create dynamic links to your Wine directory to avoid having to install again. Try the following and see how it goes:
```
wget http://thepiratecove.org/files/wine-0.9.20_wow_i386.deb
sudo apt-get --purge remove wine
sudo dpkg -i wine-0.9.15_wow_i386.deb
rm wine-0.9.15_wow_i386.deb
```

*Note: If Wine 0.9.20 doesn't work well, try the above but replace 20 with 19. Some people are reporting issues with the new version.*

Now, run winecfg from the command line and go to the Drives tab. Hit the Autodetect button. Now, go to the Audio tab and make sure OSS Driver is checked and ALSA Driver in unchacked. Close winecfg. Now you will create symbolic links from or Cedega folder to a new Wine WoW folder as well as the Cedega mozcontrol.

```
ln -s '~/.cedega/World of Warcraft/c_drive/Program Files/World of Warcraft' '~/.wine/drive_c/Program Files/World of Warcraft'

ln -s '~/.transgaming_global/mozcontrol' '~/.wine/drive_c/Program Files/mozcontrol'
```

Now, you will backup your Wine registry and copy over the Cedega registry settings to Wine.

```
cp ~/.transgaming_global/Fonts/* ~/.wine/drive_c/windows/fonts
cp ~/.wine/user.reg ~/.wine/user.reg_backup
cp ~/.wine/system.reg ~/.wine/system.reg_backup
cp ~/.wine/userdef.reg ~/.wine/userdef.reg_backup
cp ~/.cedega/World\ of\ Warcraft/*.reg ~/.wine/
```

The following will set the WoW config files to the appropriate settings to run in Wine.

```
wget http://thepiratecove.org/files/Config.WTF

mv Config.WTF ~/.cedega/World\ of\ Warcraft/c_drive/Program\ Files/World\ of\ Warcraft/WTF/Config.wtf
```

Start WoW with the following, and use it to create a menu entry is desired.

```
wine 'C:/Program Files/World of Warcraft/WoW.exe'
```

To change graphics settings you will need to start Wine in DirectX. Graphics may be messed up, but don't worry about it. It will go back to normal next time you run it normally. Run WoW in Direct X with the following.

```
wine 'C:/Program Files/World of Warcraft/WoW.exe' -d3d
```

*Note: I am actually unsure if this bug still exist.*

If you have troubles, post back here or check the [World of Warcraft wiki]("https://help.ubuntu.com/community/WorldofWarcraft").

You may also find [this thread]("http://www.ubuntuforums.org/showthread.php?t=243336") helpful.

---

### Post by Holmgreen on 2006-09-02
Thank you a LOT eqisow - i will try that out.

And as a side note: i just tried to run WoW with -D3D instead of -opengl, and it made a significant improvement to my framerate. Still... in Ironforge i'm running with around 6fps, so i guess it's still not good enough for a MC run :-)

---

### Post by ZylGadis on 2006-09-02
Um.

First, to MattKemp: memory in linux is always (or nearly always) full, because the linux kernel uses it for caching - it does not like resources sitting idle around, when they can be effectively used to improve performance. The fact that your memory is full does not at all mean that all of it is used by WoW or whatever else you are running. Try checking the usage of your particular program.

To Holmgreen: specifying the Nvidia driver may not be enough, I think. Here is the relevant section of my xorg.conf:

```
Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
	Option		"NoLogo"	"true"
	Option		"RenderAccel"	"true"
	Option		"IgnoreDisplayDevices"	"TV"
	Option		"NoRenderExtension"	"false"
	Option		"Accel"		"true"
	Option		"AllowGLXWithComposite"	"true"
	Option		"ConnectedMonitor"	"CRT,CRT"
	Option		"TwinView"	"true"
	Option		"MetaModes"	"1280x1024,1280x1024; NULL,1280x1024; NULL,1024x768"
	Option		"SecondMonitorHorizSync"	"28-64"
	Option		"SecondMonitorVertRefresh"	"43-60"
	Option		"TwinViewOrientation"		"LeftOf"
EndSection
```

You will see that some of the options are for my Twinview setup, but some are for other things. Try tweaking yours. Also, there is a guide somewhere around about enabling Side Band Addressing on Nvidias, which may or may not improve performance (in my case it does not).

I hope that helps.

---

### Post by Holmgreen on 2006-09-02
> **eqisow said:**
> 
If you have troubles, post back here or check the [World of Warcraft wiki]("https://help.ubuntu.com/community/WorldofWarcraft").


Ok - i got the Cedega installation of WoW to work through Wine. So far, thanks a lot.

Down side is that when i started WoW it only worked like 10 seconds then it crashed. Good thing is that it seemed like my framerate was improved. Wine gave me this output:

-------------------------------------------------------
```
C:/Program File s/World of Warcraft/WoW.exe' -D3D
fixme:advapi:SetSecurityInfo stub
fixme:powrprof:DllMain (0x7d160000, 1, (nil)) not fully implemented
fixme:ntdll:NtPowerInformation Unimplemented NtPowerInformation action: 11
fixme:powrprof:DllMain (0x7d160000, 0, (nil)) not fully implemented
fixme:win:EnumDisplayDevicesW ((null),0,0x33eeec,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at  the moment!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f458,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33f6f8,0x00000000), stub!
fixme:d3d:IWineD3DImpl_GetDeviceCaps Caps support for directx9 is nonexistent at  the moment!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x1b2158) : stub, simulatin g 64MB for now, returning 64MB left
fixme:d3d:IWineD3DDeviceImpl_CreateQuery (0x1b2158) Unhandled query type 8
fixme:win:EnumDisplayDevicesW ((null),0,0x33f168,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONNECT_TIMEOUT (5000): STUB
fixme:wininet:InternetSetOptionW INTERNET_OPTION_SEND/RECEIVE_TIMEOUT not suppor ted on protocol 4
fixme:wininet:InternetSetOptionW Option INTERNET_OPTION_CONTEXT_VALUE; STUB
fixme:win:EnumDisplayDevicesW ((null),0,0x33e4f8,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x33e550,0x00000000), stub!
err:seh:setup_exception stack overflow 136 bytes in thread 0009 eip 7efe3072 esp  00230f78 stack 0x231000-0x340000
err:ntdll:RtlpWaitForCriticalSection section 0x110020 "heap.c: main process heap  section" wait timed out in thread 0015, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x110020 "heap.c: main process heap  section" wait timed out in thread 0015, blocked by 0009, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x7d3f59bc "WINEOSS_msg_crst" wait timed out in thread 000f, blocked by 0010, retrying (60 sec)
err:ntdll:RtlpWaitForCriticalSection section 0x110020 "heap.c: main process heap  section" wait timed out in thread 0015, blocked by 0009, retrying (60 sec)
```
--------------------------------------------------------

I really can't make much sence of this, but i will start crawling the internet for tweak-info about Wine. Up to now i've only been reading Cedega stuff ;) 
If you have an idea how to help my Wine/WoW not to crash, i would deeply appreciate it though.

/Holmgreen

---

### Post by eqisow on 2006-09-02
Try rolling back to 0.9.19 or 0.9.18 like I suggested in my original post. I've read several reports about 0.9.20 doing odd things in WoW.

---

### Post by Holmgreen on 2006-09-02
I just tried to load WoW with -OpenGL instead of -D3D, and it helped. No crashes or strange UI clips. But... now the framerate is back on useless ](*,) 

I will try rolling Wine back a bit.

---

### Post by eqisow on 2006-09-02
Ahh, well you probably don't need to bother rolling it back then. OpenGL is what it should have been to begin with. Try messing with your in-game settings though, there are a few that really give a big performance increase in Wine, probably due to not being well supported. Unfortunately, I don't recall which ones, exactly, so you'll just have to tinker some.

---

### Post by Holmgreen on 2006-09-02
Thanks for all your help eqisow - i really appreciate it a lot.

My in-game settings is as low as it comes. I've even scaled down the resolution to 800x600. The game begins to look so ugly, that i suspect it will be hard to enjoy ;) 
Anyway... in a 40-man raid i will have a hard time seeing my own character behind all the UI-stuff that is demanded by a raid-group.

It seems like i've come down to this:

In Wine -
WoW has highest framerate running in D3D mode, but everything else is really bad. Game crash after 10 seconds
Works better in OpenGL. I have some sound issue, but my framerate is down to pretty much useless

In Cedega - 
Changing to D3D mode helped a bit, but in IronForge in rush hour, i'm down on 6-7fps. Everything else works like a charm.


My conclusion this far must be that Cedega works better for me than Wine, but it puzzles me that the framerate is so low. Playing WoW on the same machine with Windoze is totaly different when it comes to fps.

---

### Post by eqisow on 2006-09-02
Your welcome, sorry we couldn't get betetr performance for you. FYI, though, I was able to pull down 20-30 FPS in Ironforge in Wine with my GeForce 6800 128MB. They're down to about $130 bucks on Newegg, if that's worth it to you.

---

### Post by MattKemp on 2006-09-03
> **Holmgreen said:**
> Thank you a LOT eqisow - i will try that out.

And as a side note: i just tried to run WoW with -D3D instead of -opengl, and it made a significant improvement to my framerate. Still... in Ironforge i'm running with around 6fps, so i guess it's still not good enough for a MC run :-)

I've been running Naxx with 4 FPS, it doesn't help when you have giant spiders bearing down on you. :/

I just tried the D3D thing too, and it stack overflowed just inside IF, so that's not going to work for me.

> **eqisow said:**
> Your welcome, sorry we couldn't get betetr performance for you. FYI, though, I was able to pull down 20-30 FPS in Ironforge in Wine with my GeForce 6800 128MB. They're down to about $130 bucks on Newegg, if that's worth it to you.

Out of interest, could you share the rest of your setup with me? I'm thinking I've got more of a configuration problem than anything.

---

### Post by eqisow on 2006-09-03
Geforce 6800 OC 128MB
AMD64 3000+
2 GB DDR 400

The 6800 is more than twice the power of the x300 though, plus the Nvidia drivers are better.

---

### Post by Holmgreen on 2006-09-03
I've just ordered a GeForce 6200A with 256 MB DDRII RAM on it. That's what i could afford right now. I really hope that it's able to improve things enough to make the game playable on my Linux-box. I simply need to be able to play in 1024x768 resolution (i really can't do raids with 800x600), and i need my fps back... at least over 20.

Ok - once again: Thanks a bunch. I might report back if the new GeForce do the magic :cool:

---

