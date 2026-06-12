---
title: "SimCity 4 Deluxe w/ Wine"
date: 2007-05-04
forum: Gaming &amp; Leisure
---

### Post by Zayniac on 2007-05-04
I recently installed the game SimCity 4 Deluxe using wine. I managed to install it successfully, and then replaced the .exe file with a the appropriate no-cd crack. When I attempt to run the program by clicking on it, it won't run. When I run it through the terminal I do so with the following command: (after cd-ing to the appropriate folder):
[B]
wine SimCity\ 4.exe[/B]

After doing so, the screen goes black as if loading the program. It lasts like this for a few seconds, and then the black screen disappears and I'm back with my desktop. The terminal window then shows the following string:

[B]fixme:ntdll:TIME_GetTZAsStr Can't match system time zone name "IDT", bias=-180 and dst=1 to an entry in TZ_INFO. Please add appropriate entry to TZ_INFO and submit as patch to wine-patches
fixme:ntdll:TIME_GetTZAsStr Can't match system time zone name "IDT", bias=-180 and dst=1 to an entry in TZ_INFO. Please add appropriate entry to TZ_INFO and submit as patch to wine-patches
fixme:system:SystemParametersInfoW Unimplemented action: 94 (SPI_GETMOUSETRAILS)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x178278) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x176350)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1766a8)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1766a8)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x176b58)->(0x10026,00000011)
fixme:xvidmode:X11DRV_XF86VM_SetCurrentMode Cannot change screen BPP from 32 to 16
fixme:d3d:IWineD3DDeviceImpl_CreateAdditionalSwapChain The app requests more than one back buffer, this can't be supported properly. Please configure the application to use double buffering(=1 back buffer) if possible
fixme:d3d_surface:IWineD3DSurfaceImpl_LockRect Depth stencil locking not supported yet
fixme:d3d_surface:IWineGDISurfaceImpl_Blt Can't handle DDBLT_ASYNC flag right now.
fixme:d3d_surface:IWineD3DSurfaceImpl_UnlockRect Depth Stencil buffer locking is not implemented
fixme:d3d_surface:IWineD3DSurfaceImpl_LockRect Depth stencil locking not supported yet
fixme:d3d_surface:IWineD3DSurfaceImpl_UnlockRect Depth Stencil buffer locking is not implemented
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x13a0028)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x1530030)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
fixme:wave:DSD_CreateSecondaryBuffer (0x2084c0,0x33fbf4,8014,0,0x1141fa4,0x11420b4,0x1141f80): stub
fixme:wave:DSD_CreateSecondaryBuffer (0x2084c0,0x33fc90,18000,0,0x1141fa4,0x1142154,0x1141f80): stub[/B]


A few more details about my system:

CPU: Intel Pentium IV 2.6 Ghz
Graphics card: Nvidia GeForce 4 Ti-4200
OS: Ubuntu Feisty Fawn 7.04

Also, I'm trying to run the software w/o the compiz effects enabled.



Can anyone help me with this?

Please also take into consideration that I'm pretty new with both Linux and WINE, so when helping, it would be great if done as if speaking to a 6 year old. :-) 


Thank you all in advance!

---

### Post by feest on 2007-05-04
wine is not campatible with all games please remember that... I don't know if this game has been run succesfully by a wine tester you can look that up on appdb.winehq.com, also if there is a topic about simcity 4 on winehq, read it... sometimes howto' are included...

---

### Post by mistergq on 2007-05-05
have you tried this how to?
[http://www.simpage.net/simcity4/articles/1054017182.shtml](http://www.simpage.net/simcity4/articles/1054017182.shtml)

---

### Post by scotty2hott2k on 2007-05-05
just looked on wine app database, try running with the command:

wine SimCity\ 4.exe -d:opengl -intro:off

(obviously need to cd into the fodler where the .exe is located)

---

### Post by Zayniac on 2007-05-06
I did try that command, it actually didn't run the program properly, only made my Gnome to get all buggy...

---

### Post by Breepee on 2007-05-06
Doesn't work here either and I think is has something to do with versions. Appdb lists older versions as working so I assume there've been regression of some sort.

---

### Post by rai4shu2 on 2007-05-06
I don't have Deluxe (still playing the original base SC4 version), but it is a bit of a chore:

```
cd ~/.wine/drive_c/Program\ Files/Maxis/SimCity\ 4/Apps/
wine explorer /desktop=SC4,1024x768 Simcity\ 4.exe -intro:off >/dev/null 2>&1
```

---

### Post by Zayniac on 2007-05-06
With that code, a window opens and the program seems to start running, but it has the same effect:

black screen for a few seconds, and then the window closes. 

The interesting part is that the terminal doesn't spit out all the "fixme"'s. In fact, it doesn't spit out anything....

---

### Post by edemark on 2007-05-06
Do you know this site?

[http://frankscorner.org/index.php?p=simcity4](http://frankscorner.org/index.php?p=simcity4)

good luck

---

### Post by Uodnelome on 2007-05-06
I believe the Simpage.net tutorial refers to the original release of SimCity 4, not the deluxe version.  Perhaps enough has changed with the compilation of the Rush Hour expansion pack and the original into a single page that what made SimCity 4 work with Wine no longer holds true for the Deluxe version.

The resource on Frank's Corner is for SimCity 4 as well.  That said, with few-to-no online solutions for getting SimCity 4 Deluxe to work, it can't hurt to give any of them a try at least.

---

### Post by spvo on 2007-05-19
With Edgy SimCity 4 Deluxe worked perfect for me.  I didn't even have to add anything special to the wine command to run it.  It was reasonably buggy tho, a lot of the rush hour components would cause the game to crash.

---

### Post by nicolasdiogo on 2011-05-30
one thing i noticed while using PlayOnLinux to install the game is that there is a problem when it asks for the second disc (disk 2).

it waits to have disc 2 mounted at the same location as disc 1.
since ubuntu creates mount point with the name of the CD - your first disk was mounted in SC4DELUXE1 and disc 2 is mounted in SC4DELUXE2. so you have to create a symbolic link to solve this problem.

```

cd /media
sudo ln -s SC4DELUXE2/ SC4DELUXE1

```


when you completed the installation, remove the link with:
```

cd /media
rm SC4DELUXE1

```

---

### Post by Perfect Storm on 2011-05-30
Necromancing (2007). Thread closed.

R.I.P.

---

