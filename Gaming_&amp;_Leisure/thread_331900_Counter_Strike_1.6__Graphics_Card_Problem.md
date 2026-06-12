---
title: "Counter Strike 1.6 / Graphics Card Problem"
date: 2007-01-05
forum: Gaming &amp; Leisure
---

### Post by encikraju on 2007-01-05
I have installed successfully using wine but the game wont' load and error of 
software mode keep popped out everytime I hit 'OK' button.
This is what on terminal.

fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x168f58) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x166c78)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x166c78)->((nil),00000013)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x166c78)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock


Really2 need help.

---

### Post by hikaricore on 2007-01-05
I know counter strike source is supposed to work with wine, but I honestly know nothing of the game if your version will work.
Here's the [wine application database's page for CS:S]("http://appdb.winehq.org/appview.php?iAppId=871") hopefully this can get you started in the right direction.

Also is your video card working?  Have you successfully played native games that require direct rendering?

Open a terminal and type:

```
glxinfo | grep rendering
```

To see if your video drivers are properly installed.  This should return a: YES

---

### Post by encikraju on 2007-01-06
thanks for reply. YES. My graphics card is working. 
Anyway, how to uninstall Counter Strike from wine?

---

### Post by encikraju on 2007-01-10
Come on come on really2 wanna play counter strike, This is my error after I re-do everything.

```
fixme:seh:check_no_exec No-exec fault triggered at 0x1e61e39, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e66609, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e5f4b0, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e69fac, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e656d3, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e6a01e, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e6d0f2, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e64704, enabling work-around
fixme:seh:check_no_exec No-exec fault triggered at 0x1e6cea5, enabling work-around
err:seh:setup_exception nested exception on signal stack in thread 0009 eip 7efd4b73 esp 7ffddbf0 stack 0x231000-0x340000

```

---

### Post by Brynster on 2007-01-10
What Video card are you running and which instructions did you use to install it.

I am running Counterstrike 1.6 and it run 99% perfectly (small font issue in console is the only problem). If that fills you with hope. I just need more info before we can go further.

---

### Post by Enverex on 2007-01-10
You're running 64bit aren't you? This is the NX extension kicking in and stopping 32bit code from executing. It affects a few games in Wine and seems to be related to copy protection oddly enough. Anyway, to get around this you need to add 'noexec32=off' to your kernel boot line then it will work fine.

---

### Post by encikraju on 2007-01-11
Thanks for reply. I'm using Edgy 64 and setup my graphics driver from ubuntuguide.org
ATI Driver (Radeon 9600).
Now i'm using wine 0.9.24

How to edit kernel boot line?Sorry...

Thanks.

Upgraded to 0.9.28 and got this error when running hl.exe
```
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x168f68) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x166c88)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x166c88)->((nil),00000013)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x166c88)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
```

---

### Post by Enverex on 2007-01-11
Lets fix one problem at a time shall we. To edit the Kernel boot line you can either do it in a one-off fashion by; when your computer boots and you get presented with the Grub list, select the one you normally boot, then press "e" and add "noexec32=off" to the line that starts with "kernel=".

The second problem is self explanitory. Open winecfg and change the Hardware Accelleration to Emulation like it says.

---

### Post by encikraju on 2007-01-11
Thanks for your reply. I will give a try when I boot my pc.8)

---

### Post by cocotapioca on 2007-01-16
i have a problem, i dont see any font, text in the dialogs.
ex: in the options dialog i only see the spray logo image (and hte components like combo box and etc, but no text).

---

### Post by encikraju on 2007-01-22
Enverex, i have tried the noexec32=off but seems does not working for me.
The uotput is

```
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x167648) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x166d70)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x166d70)->((nil),00000013)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x166d70)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
err:dsound:DSOUND_MixOne underrun on sound buffer 0x183d08

```

And here the screenshot of it.

---

### Post by maximi89 on 2007-02-03
> **encikraju said:**
> I have installed successfully using wine but the game wont' load and error of 
software mode keep popped out everytime I hit 'OK' button.
This is what on terminal.

fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x168f58) : stub, simulating 64MB for now, returning 64MB left
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x166c78)->((nil),00000008)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x166c78)->((nil),00000013)
fixme:ddraw:IDirectDrawImpl_SetCooperativeLevel (0x166c78)->((nil),00000008)
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock


Really2 need help.
Hola, u need go to winecfg, and to Audio, and try this, all Plugins of audio don't selected...
try that and post...

---

### Post by Enverex on 2007-02-03
You need to update your graphics drivers, seems you're using the old broken 8776 nVidia drivers (for Christs sake Ubuntu, update Edgy to use the new ones, the old ones are BROKEN).

For the "no text" issue you need to put the Tahoma font in the windows/fonts folder.

---

### Post by encikraju on 2007-02-07
Thanks for reply. Anyway, I reinstall and dl .ttf and everything works fine but i can't change the reso from 1280x1024 to 800x600(no selection in Optoins menu). Anyone know how to change the reso?

---

### Post by Enverex on 2007-02-07
You're probably using the broken nVidia drivers that ship with Ubuntu Edgy. Update them.

---

