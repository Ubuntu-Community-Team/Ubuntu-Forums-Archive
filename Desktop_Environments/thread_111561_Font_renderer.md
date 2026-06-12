---
title: "Font renderer"
date: 2006-01-02
forum: Desktop Environments
---

### Post by rjwood on 2006-01-02
I got cute with my desktop and installed some themes that didnt belong. I can not log in under my name and the error says font renderer is set to "0". Any Idea's??

---

### Post by 23meg on 2006-01-02
Where do you get that error? What exactly happens afterwards? Which themes did you install and how?

---

### Post by rjwood on 2006-01-02
Thanks 23meg!!  I install some gtk themes through synaptic. They were listed as gnome themes but they were older I think. When I set one to work, first my clock disappeared and an error message appeared. then I rebooted but x won't start. I reconfigured xserver a few times but no good.  It seems that if I were able to get in< I would need to set font render up through systems>preferences>fonts but, I dont know how to do that from the command line.  Here is the dreaded log file. Sorry to do that to you.


 
  
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
    Entry deleted from font path.
(WW) The directory "/usr/share/X11/fonts/CID" does not exist.
    Entry deleted from font path.
(WW) `fonts.dir' not found (or not valid) in "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID".
    Entry deleted from font path.
    (Run 'mkfontdir' on "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID").
(**) FontPath set to "/usr/share/X11/fonts/misc,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
(==) RgbPath set to "/usr/X11R6/lib/X11/rgb"
(==) ModulePath set to "/usr/X11R6/lib/modules"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) Module ABI versions:
 (II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "640x480" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "320x240" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "800x600" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "400x300" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "512x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "512x384" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x960" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "928x696" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "832x624" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "416x312" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1152x768" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "576x384" (vrefresh out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1680x1050" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "840x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "960x720" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1024x768" (bad mode clock/interlace/doublescan)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(**) NVIDIA(0): Validated modes for display device DFP-0:
(**) NVIDIA(0):      Default mode "1280x1024": 108.0 MHz, 64.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x960": 108.0 MHz, 60.0 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x800": 83.5 MHz, 49.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1280x768": 80.1 MHz, 47.7 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): Display dimensions: (390, 290) mm
(--) NVIDIA(0): DPI set to (83, 89)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/X11R6/lib/modules/libfb.a
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
(II) Module fb: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 1.0.0
    ABI class: X.Org ANSI C Emulation, version 0.2
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/X11R6/lib/modules/libramdac.a
(II) Module ramdac: vendor="X.Org Foundation"
    compiled for 6.8.2, module version = 0.1.0
    ABI class: X.Org Video Driver, version 0.7
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
    [0] 0    0    0xe0000000 - 0xefffffff (0x10000000) MX[b]
    [1] 0    0    0xfc000000 - 0xfcffffff (0x1000000) MX[b]
    [2] -1    0    0xffe00000 - 0xffffffff (0x200000) MX[b](B)
    [3] -1    0    0x00100000 - 0x3fffffff (0x3ff00000) MX[b]E(B)
    [4] -1    0    0x000f0000 - 0x000fffff (0x10000) MX[b]
    [5] -1    0    0x000c0000 - 0x000effff (0x30000) MX[b]
    [6] -1    0    0x00000000 - 0x0009ffff (0xa0000) MX[b]
    [7] -1    0    0xfb600000 - 0xfb6000ff (0x100) MX[b]
    [8] -1    0    0xfb800000 - 0xfb8003ff (0x400) MX[b]
    [9] -1    0    0xfe400000 - 0xfe40003f (0x40) MX[b]
    [10] -1    0    0xfe500000 - 0xfe5007ff (0x800) MX[b]
    [11] -1    0    0xfe600000 - 0xfe600fff (0x1000) MX[b]
    [12] -1    0    0xfe800000 - 0xfe800fff (0x1000) MX[b]
    [13] -1    0    0xfeb00000 - 0xfeb000ff (0x100) MX[b]
    [14] -1    0    0xfea00000 - 0xfea00fff (0x1000) MX[b]
    [15] -1    0    0xfe900000 - 0xfe900fff (0x1000) MX[b]
    [16] -1    0    0xf4000000 - 0xf3ffffff (0x0) MX[b]O
    [17] -1    0    0xfda00000 - 0xfda1ffff (0x20000) MX[b](B)
    [18] -1    0    0xe0000000 - 0xefffffff (0x10000000) MX[b](B)
    [19] -1    0    0xfc000000 - 0xfcffffff (0x1000000) MX[b](B)
    [20] 0    0    0x000a0000 - 0x000affff (0x10000) MS[b](OprD)
    [21] 0    0    0x000b0000 - 0x000b7fff (0x8000) MS[b](OprD)
    [22] 0    0    0x000b8000 - 0x000bffff (0x8000) MS[b](OprD)
    [23] -1    0    0x0000ffff - 0x0000ffff (0x1) IX[b]
    [24] -1    0    0x00000000 - 0x000000ff (0x100) IX[b]
    [25] -1    0    0x0000d400 - 0x0000d4ff (0x100) IX[b]
    [26] -1    0    0x0000dc00 - 0x0000dc07 (0x8) IX[b]
    [27] -1    0    0x0000d800 - 0x0000d8ff (0x100) IX[b]
    [28] -1    0    0x0000ffa0 - 0x0000ffaf (0x10) IX[b]
    [29] -1    0    0x0000ef00 - 0x0000ef7f (0x80) IX[b]
    [30] -1    0    0x0000e000 - 0x0000e0ff (0x100) IX[b]
    [31] -1    0    0x0000e880 - 0x0000e887 (0x8) IX[b]
    [32] -1    0    0x0000ec00 - 0x0000ec1f (0x20) IX[b]
    [33] 0    0    0x000003b0 - 0x000003bb (0xc) IS[b](OprU)
    [34] 0    0    0x000003c0 - 0x000003df (0x20) IS[b](OprU)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "UseFBDev" is not used
(==) RandR enabled
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
Symbol __glXgetActiveScreen from module /usr/X11R6/lib/modules/extensions/libdri.a is unresolved!
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension LBX
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(II) Initializing extension GLX
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 5
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
(II) NVIDIA(0): Setting mode "1024x768"
(WW) Open APM failed (/dev/apm_bios) (No such file or directory)
(II) NVIDIA(0): Setting mode "1280x1024"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(**) NVIDIA(0): DPMS enabled
(==) RandR enabled
(II) Initializing extension GLX
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) NVIDIA(0): Setting mode "1024x768"

---

### Post by 23meg on 2006-01-02
Which packages are these? Remove them if you haven't and try ```
sudo dpkg-reconfigure fontconfig
```

---

### Post by rjwood on 2006-01-02
No good---When I try to log in, I only get the blue/grey 'x' screen. The panel comes up (blank) and then I hear the sound of error messages coming up but no visuals. I did remove all the themes through the root account. I am wondering if It lacks a theme now although It is still behaving the same as before. All othe user accounts work fine, but then I didn't mess with them.:cool: Error message is still the same.

---

### Post by rjwood on 2006-01-03
Fixed it--I installed xubuntu and signed into that. It didnt want me to get to any of the settings but, it let me get to synaptic and I removed all the recently installed themes an extras. Rebooted and everything was ok. I don't know which one gave me the problem. It was a theme though. Thanks for the help 23meg.

---

