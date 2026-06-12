---
title: "Counter Strike crashes hard"
date: 2006-10-29
forum: Gaming &amp; Leisure
---

### Post by superheavy on 2006-10-29
I am using wine (wine 9.23) to run Counter Strike 1.6 under steam.  My kernel is 2.6.15. Sometimes, which appears to be a random occurrence, my system freezes, and when it crashes it crashes hard.  I  have to restart my computer by unplugging it.  Where can I find a dump of some kind to give me any information to find out what is happening.  Any help is greatly appreciated

---

### Post by cos4 on 2006-12-29
I've got exactly the same problem. Someone from a german forum said I should try booting with acpi=off but unfortunately that causes a kernel panic. Maybe it works for you. 

I'm still looking for a solution, anyone an idea?

EDIT:I just created an errorlog using **$nice -n 20 wine Steam.exe 2>error.log** here is the result
> $ tail error.log
fixme:shdocvw:OleObject_Close (0x731c498)->(1)
fixme:mshtml:HlinkTarget_SetBrowseContext (0x731cce0)->((nil))
fixme:shdocvw:ViewObject_Draw (0x210ed8)->(1 -1 (nil) (nil) 0x99c 0xc50 0x34f9b0 (nil) (nil) 00000000)
err:mshtml:nsIOService_NewURI Could not get nsIWineURI: 80004002
fixme:shdocvw:ViewObject_Draw (0x210ed8)->(1 -1 (nil) (nil) 0x99c 0xd10 0x34f9b0 (nil) (nil) 00000000)
fixme:msg:handle_internal_message unknown internal message ffffffff
fixme:msg:handle_internal_message unknown internal message ffffffff
err:virtual:NtQueryVirtualMemory Unsupported on other process
err:virtual:NtQueryVirtualMemory Unsupported on other process
err:ntdll:RtlpWaitForCriticalSection section 0x7e569160 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0017, blocked by 0009, retrying (60 sec)
If needed I can post the full errorlog.

---

### Post by JeanJean on 2006-12-29
For me steam works fine, only when I try to minimize steam my Xorg crashes, but thats a bug.

---

### Post by cos4 on 2006-12-29
I search via google for the error and found a lot. It seems to be caused by OpenGL, non-native libs and ATI/fglrx
So I post some more info here(may the bold part of my xorg.conf has anything to do with it?)
```
Section "Device"

    # vendor=1002, device=4e49
	Identifier  "ATI Graphics Adapter"
	Driver      "fglrx"
	Option	    "no_accel" "no"
	Option	    "no_dri" "no"
# === misc DRI settings ===
	Option	    "mtrr" "off" # disable DRI mtrr mapper, driver has its own code for mtrr
	Option	    "DesktopSetup" "(null)"
	Option	    "ScreenOverlap" "0"
	Option	    "GammaCorrectionI" "0x00000000"
	Option	    "GammaCorrectionII" "0x00000000"
# === OpenGL specific profiles/settings ===
	Option	    "Capabilities" "0x00000000"
	Option	    "CapabilitiesEx" "0x00000000"
# === Video Overlay for the Xv extension ===
	Option	    "VideoOverlay" "on"
[B]# === OpenGL Overlay ===
	Option	    "OpenGLOverlay" "off"[/B]
# === Center Mode (Laptops only) ===
	Option	    "CenterMode" "off"
# === Pseudo Color Visuals (8-bit visuals) ===
	Option	    "PseudoColorVisuals" "off"
# === QBS Management ===
	Option	    "Stereo" "off"
	Option	    "StereoSyncEnable" "1"
# === FSAA Management ===
	Option	    "FSAAEnable" "no"
	Option	    "FSAAScale" "1"
	Option	    "FSAADisableGamma" "no"
	Option	    "FSAACustomizeMSPos" "no"
	Option	    "FSAAMSPosX0" "0.000000"
	Option	    "FSAAMSPosY0" "0.000000"
	Option	    "FSAAMSPosX1" "0.000000"
	Option	    "FSAAMSPosY1" "0.000000"
	Option	    "FSAAMSPosX2" "0.000000"
	Option	    "FSAAMSPosY2" "0.000000"
	Option	    "FSAAMSPosX3" "0.000000"
	Option	    "FSAAMSPosY3" "0.000000"
	Option	    "FSAAMSPosX4" "0.000000"
	Option	    "FSAAMSPosY4" "0.000000"
	Option	    "FSAAMSPosX5" "0.000000"
	Option	    "FSAAMSPosY5" "0.000000"
# === Misc Options ===
	Option	    "UseFastTLS" "0"
	Option	    "BlockSignalsOnLock" "on"
	Option	    "UseInternalAGPGART" "yes"
	Option	    "ForceGenericCPU" "no"
	BusID       "PCI:1:0:0"

EndSection

Section "Extensions"
Option "Composite" "Disable"
EndSection
```
```
$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Generic
OpenGL version string: 2.0.6011 (8.28.8)
```
```
~$ uname -r
2.6.17-10-generic
```

Regrettably I didn't found a solution so far, so help is still needed, anyone further ideas, assumptions...?

---

