---
title: "star wars knights of the old republic"
date: 2007-09-22
forum: Gaming &amp; Leisure
---

### Post by PurposeOfReason on 2007-09-22
I've seen people with screens of KOTOR under wine so I decided to get out my copy and try to install it. It installed fine, updated fine, but didn't run so I got a no cd crack so that got fixed. However, it won't run so I checked the config options and had it scan my hardware. It's complaing about nvidia drivers not being up to date. It's a Nvidia geforce 7600. I would imagine that it's more of a regedit type fix but I don't know much about wine so any help is welcome. :)

---

### Post by cogadh on 2007-09-22
Don't bother with the system scan, it is always going to fail since it is looking for Windows drivers, which are obviously not present in Linux. The game itself will work however.

On my system, I didn't have to do anything special at all to get it to run. Are you getting any error messages in the terminal when you try to run it?

---

### Post by PurposeOfReason on 2007-09-22
Here is the full output.

```
shawn@Desktop:~$ wine '/home/shawn/.wine/drive_c/Program Files/LucasArts/SWKotOR/swkotor.exe'
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:dsalsa:SetFormat Your alsa dmix period size is 1024, try decreasing it to 512 if possible
err:wgl:X11DRV_wglGetProcAddress (wglCreateBufferRegionARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglDeleteBufferRegionARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglSaveBufferRegionARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglRestoreBufferRegionARB) - not found
fixme:wgl:X11DRV_wglChoosePixelFormatARB unused pfAttribFList
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  144 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  179
  Current serial number in output stream:  179
shawn@Desktop:~$ 

```

---

### Post by cogadh on 2007-09-22
One minor thing, you should cd to the games install directory before you run it and you should run the launcher app and not the game executable:
```
cd /home/shawn/.wine/drive_c/Program Files/LucasArts/SWKotOR
wine launcher.exe

```
However, the errors you posted seem to indicate a graphics problem. Do you have the Nvidia 3D accelerated drivers installed?

---

### Post by PurposeOfReason on 2007-09-22
I used the restricted driver manager to enable it.

---

### Post by cogadh on 2007-09-22
Run this in a terminal and post the results:
```
glxinfo | grep direct
```

---

### Post by PurposeOfReason on 2007-09-22
```
shawn@Desktop:~$ glxinfo | grep direct
direct rendering: Yes

```

---

### Post by cogadh on 2007-09-22
Hmmm, what version of Wine are you using?

---

### Post by PurposeOfReason on 2007-09-22
9.42 64bit version. Should I get a newer or older one?

---

### Post by PurposeOfReason on 2007-09-22
I'm going back to 0.9.39 to see if that does it.

EDIT - that did it! :)

---

### Post by cogadh on 2007-09-22
Great, not sure I really helped much, but I'm glad it works now!

---

### Post by PurposeOfReason on 2007-09-22
I'll try that too in a little bit. Though as it's working with 0.9.39, I'm not complaining.

---

### Post by PurposeOfReason on 2007-09-22
Well now it runs, but it locks up everything after I get through the opening scene. Sometimes not even that far.

---

### Post by cogadh on 2007-09-22
Well, I originally deleted this after I saw you got the game working, but this might help. Change the DirectDraw renderer in Wine from GDI to OpenGL:

[list=1]
[*]Run "regedit" in the terminal
[*]Navigate through the file tree to HKEY_CURRENT_USER/Software/Wine
[*]Create a new Key within the Wine Key called "Direct3D"
[*]Create a new String Value within the Direct3D Key called "DirectDrawRenderer"
[*]Set the String's value to "opengl"
[/list]
Exit regedit and try rerunning the game.

---

### Post by PurposeOfReason on 2007-09-22
That seems to have helped thought is still froze everything. So then on restart, I disabled compiz, didn't have amarok running, and it seems to have worked. I'll report back.

---

### Post by cogadh on 2007-09-22
Ah, you didn't mention Compiz before (or did I just miss it?). Compiz and Beryl both can conflict with games running through Wine and shouldn't be used while running them. I'm not sure if the same is true for Compiz Fusion, though.

---

### Post by hillahilla on 2007-10-20
Hi everyone,

With Wine 0.9.45 the launcher starts then attempting to launch the game closes the Wine desktop with the following messages:

```
fixme:system:Sy
stemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
err:ole:COMPOBJ_DllList_Add couldn't load in-process dll L"a3dapi.dll"
err:ole:CoGetClassObject no class object {92fa2c24-253c-11d2-90fb-006008a1f441}
could be created for context 0x1
fixme:x11drv:X11DRV_desktop_SetCurrentMode Cannot change screen BPP from 16 to 3
2
wine: Unhandled page fault on read access to 0x00000000 at address 0x49b48e (thr
ead 0012), starting debugger...
err:dsound:DSOUND_MixOne Fatal error. Under/Overflow? primary_done=62720, mixpos
=58624/147456 (58624/147456), primary_mixpos=9472, writepos=12288, mixlen=8192
```

any suggestions?
thanks!

---

### Post by cogadh on 2007-10-20
If you updated the game to 1.03, then you will need to use a cracked executable, due to Wine's lack of copy protection support. That limit sometimes presents itself as an unhandled page fault.

I also wonder about those other errors. The first one would seem to indicate some kind of graphics error. Do you have the accelerated driver for your video card installed? The second one is obviously a sound error. What are your sound settings in winecfg?

---

### Post by hillahilla on 2007-10-21
thanks, man!
i checked the nvidia settings and it seems the glx wasn't in use... so i restarted the x-server twice and now it works like a charm.

i still don't have sound, wine is set on alsa.

anyway, thank you!

---

### Post by cogadh on 2007-10-21
Sound is occasionally intermittent with this game (doesn't work at all the first time you launch it, works great the next time). I've never been able to get that to stop happening, but sound does work more often than not for me. I keep my sound set for ALSA, hardware acceleration at full, sample rate at 48 kHz, bit depth at 16 and driver emulation is not checked. You might try out those settings and see if they work for you.

---

### Post by hillahilla on 2007-10-21
oh, actually it's quite funny. first time it didn't have any sound so i just figured i'd listen to some music instead. xmms not working (some other program using the soundcard), so next time i started xmms and then kotor. and guess what... kotor sound now working.

weird.

though, in retrospect, i'd rather listen to the flaming lips than to the sound of plasteel containers open.

thanks!

---

### Post by cogadh on 2007-10-21
I had something very similar happen with Neverwinter Nights native client. Sound in cutscenes would only work if I had my Last.FM player running first. It didn't have to actually be playing music, it just had to be running. It was obviously a problem with the software sound mixing and I ended up fixing it by modifying NWN's launch script to specify a sound mixer, but I'm not sure how you could do the same with with a game launched through Wine... I think I'll have to research this a bit.

---

### Post by stueytheboy on 2009-05-25
Hi,

I saw your posts and was wondering if I could get some help. I'm trying to get Kotor 2 to work. I'm fairly new to ubuntu but I was able to get it installed using wine (not sre what version or how to find out). When I start the game now it plays the LucasArts logo almost right away, then it flips between a full black screen and my desktop with a black window in it. it does this for a few minutes then plays the obsidian logo and goes to a bad graphics version of the main menu. Any tips?

---

