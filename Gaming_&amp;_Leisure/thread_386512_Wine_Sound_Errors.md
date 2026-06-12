---
title: "Wine Sound Errors"
date: 2007-03-17
forum: Gaming &amp; Leisure
---

### Post by ac336 on 2007-03-17
Hi, only just installed linux for the first time and trying to get wine & wow to work.  Using an AMD64 if that makes a difference, wine version 0.9.32.  When installing WoW I got this error:

```
Missing symbol {Error%dOpening%s}! (SymbolTable::UnmappedSymbolSubstitution)
Missing symbol {ContactTechSupport}! (SymbolTable::UnmappedSymbolSubstitution)
fixme:font:CreateScalableFontResourceW (1,0x145e208,0x145a308,(nil)): stub
andy@andy-desktop:~/WorldofWarcraft$ fixme:richedit:IRichEditOle_fnGetClientSite stub 0x17f3280
fixme:ole:OleCreateStaticFromData (not shown), stub!
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:winmm:MMDRV_Exit Closing while ll-driver open
fixme:win:EnumDisplayDevicesW ((null),0,0x34f230,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34eee0,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f6ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34f6ec,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ee5c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x172e50) : stub, simulating 64MB for now, returning 64MB left
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (XRandR)
fixme:win:EnumDisplayDevicesW ((null),0,0x34ee5c,0x00000000), stub!
fixme:system:SystemParametersInfoW Unimplemented action: 112 (SPI_GETMOUSESPEED)
fixme:system:SystemParametersInfoW Unimplemented action: 113 (SPI_SETMOUSESPEED)
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:wave:DSDB_MapBuffer Could not map sound device for direct access (Input/output error)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.

```

And now, I've opened up winecfg and as soon as I click on the Audio tab, I get this in my terminal window:

```
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: wrong ELF class: ELFCLASS64
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
err:module:load_builtin_dll failed to load .so lib for builtin L"winenas.drv": libaudio.so.2: wrong ELF class: ELFCLASS64
ALSA lib ../../../src/seq/seq_hw.c:457:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

```

Any ideas what I've missed or how I can fix this?  I changed it to 'emulation' as it says, but when I try to run WoW itself, all that happens is I get some crackly noises and nothing appears on screen.

I found a page with instructions on copying the libjack0.100.0.0.so which I followed but it doesn't seem to have made any difference.

---

### Post by john_g on 2007-03-17
I had to go to the /usr/lib directory and add a link to libjack-0.100.0.so.0.0.23 so wine could find it.  

    sudo ln -s libjack-0.100.0.so.0.0.23 libjack.so

Sound now works in wine.   Of course, libjack needs to be there. 

 --john g

---

### Post by cd7 on 2007-03-18
I fixed the ALSA issue with:
```
sudo modprobe snd-seq
```

dario

---

