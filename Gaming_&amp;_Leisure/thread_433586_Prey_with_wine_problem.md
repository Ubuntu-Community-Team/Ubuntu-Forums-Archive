---
title: "Prey with wine problem"
date: 2007-05-05
forum: Gaming &amp; Leisure
---

### Post by wInddnIw on 2007-05-05
Hi,

  I am running Ubuntu Feisty Fawn 7.04 64bit (kernel 2.6.20-15-generic) with latest wine-0.9.36 and latest nvidia drivers installed using envy. My gc is a GeForce 7600 GT.

  I try to run the game prey but have a lot of problems... The game is running fine under windows though.

  The latest problem is a "Unable to initialize OpenGL". Here is the console output : 
```
# wine prey.exe 
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:create_server class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x15
err:wgl:X11DRV_wglGetProcAddress (wglBindTexImageARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleaseTexImageARB) - not found
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)
err:wgl:X11DRV_wglGetProcAddress (wglBindTexImageARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleaseTexImageARB) - not found
err:x11settings:X11DRV_ChangeDisplaySettingsEx No matching mode found! (NoRes)
```

After searching the forum and the net, it seems to come from a missing resolution in my xorg.conf. But everything seems ok inside my xorg.conf : ```
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
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
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
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Buttons" "5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

Section "InputDevice"

							# /dev/input/event
							# for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"	# Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"

							# /dev/input/event
							# for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"	# Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"

							# /dev/input/event
							# for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"	# Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x768" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x768" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x768" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x768" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x768" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x768" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```

Btw, glxgears answer "50462 frames in 5.0 seconds = 10092.367 FPS" which seems to be rather enough for prey.

Any idea ?

wInd

---

### Post by wInddnIw on 2007-05-07
Nobody as any idea or hint on how to solve this ?
Please !

wInd

---

### Post by crane on 2007-05-07
hmmmm, I'm not real sure on this. When you ran winesetup what os did you set it to? If you set it to XP try changing it to 2000.

---

### Post by wInddnIw on 2007-05-08
Hi, 
 Thanks for your answer !
  It was on win98. I tried with windows XP and 2000 with the same result.
  But I found a way to go over this problem by setting wine to create a virtual desktop of 1024x768. But then I have this error : 

```
$ wine prey.exe 
err:ole:CoGetClassObject class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
err:ole:create_server class {4590f811-1d3a-11d0-891f-00aa004b2e24} not registered
fixme:ole:CoGetClassObject CLSCTX_REMOTE_SERVER not supported
err:ole:CoGetClassObject no class object {4590f811-1d3a-11d0-891f-00aa004b2e24} could be created for context 0x15
err:wgl:X11DRV_wglGetProcAddress (wglBindTexImageARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleaseTexImageARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglBindTexImageARB) - not found
err:wgl:X11DRV_wglGetProcAddress (wglReleaseTexImageARB) - not found
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
wine: Unhandled page fault on execute access to 0x00000000 at address (nil) (thread 000d), starting debugger...
Unhandled exception: page fault on execute access to 0x00000000 in 32-bit code (0x00000000).
Register dump:
 CS:0023 SS:002b DS:002b ES:002b FS:0063 GS:006b
 EIP:00000000 ESP:03d4d9a4 EBP:055c0040 EFLAGS:00210246(   - 00      -RIZP1)
 EAX:03d500e0 EBX:00200000 ECX:00200000 EDX:fffffffe
 ESI:049934b4 EDI:017fa290
Stack dump:
0x03d4d9a4:  004fa6d8 00008892 03d500e0 017fa2b4
0x03d4d9b4:  017fa290 00000002 004facf6 055c0040
0x03d4d9c4:  00000000 017fa2b4 00000000 03d40001
0x03d4d9d4:  007b027c 03d4fe50 00000000 004c3241
0x03d4d9e4:  007b4894 0094dd70 00000000 00001000
0x03d4d9f4:  03d4da0c 007b4894 03d40001 00000000
Backtrace:
=>1 0x00000000 (0x055c0040)
  2 0x00000000 (0x00000000)
0x00000000: addb        %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (92 modules)
PE        400000- 3838000       Deferred        prey
ELF     7b800000-7b927000       Deferred        kernel32<elf>
  \-PE  7b820000-7b927000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7e1bc000-7e1ee000       Deferred        uxtheme<elf>
  \-PE  7e1c0000-7e1ee000       \               uxtheme
ELF     7e1ee000-7e214000       Deferred        msacm32<elf>
  \-PE  7e200000-7e214000       \               msacm32
ELF     7e214000-7e22c000       Deferred        msacm32<elf>
  \-PE  7e220000-7e22c000       \               msacm32
ELF     7e22c000-7e268000       Deferred        wineoss<elf>
  \-PE  7e230000-7e268000       \               wineoss
ELF     7e268000-7e26d000       Deferred        libxfixes.so.3
ELF     7e26d000-7e276000       Deferred        libxcursor.so.1
ELF     7e276000-7e27e000       Deferred        libxrender.so.1
ELF     7e27e000-7e29b000       Deferred        imm32<elf>
  \-PE  7e290000-7e29b000       \               imm32
ELF     7e29b000-7e329000       Deferred        winex11<elf>
  \-PE  7e2b0000-7e329000       \               winex11
ELF     7e329000-7e33d000       Deferred        libz.so.1
ELF     7e33d000-7e3a7000       Deferred        libfreetype.so.6
ELF     7e3a7000-7e3bc000       Deferred        midimap<elf>
  \-PE  7e3b0000-7e3bc000       \               midimap
ELF     7e3bc000-7e3d0000       Deferred        oleacc<elf>
  \-PE  7e3c0000-7e3d0000       \               oleacc
ELF     7e3d0000-7e3f2000       Deferred        oledlg<elf>
  \-PE  7e3e0000-7e3f2000       \               oledlg
ELF     7e3f2000-7e43b000       Deferred        dsound<elf>
  \-PE  7e400000-7e43b000       \               dsound
ELF     7e43b000-7e471000       Deferred        dinput<elf>
  \-PE  7e440000-7e471000       \               dinput
ELF     7e471000-7e50c000       Deferred        oleaut32<elf>
  \-PE  7e480000-7e50c000       \               oleaut32
ELF     7e50c000-7e561000       Deferred        rpcrt4<elf>
  \-PE  7e520000-7e561000       \               rpcrt4
ELF     7e561000-7e5fe000       Deferred        ole32<elf>
  \-PE  7e570000-7e5fe000       \               ole32
ELF     7e5fe000-7e631000       Deferred        winspool<elf>
  \-PE  7e610000-7e631000       \               winspool
ELF     7e631000-7e6ed000       Deferred        comctl32<elf>
  \-PE  7e640000-7e6ed000       \               comctl32
ELF     7e6ed000-7e745000       Deferred        shlwapi<elf>
  \-PE  7e700000-7e745000       \               shlwapi
ELF     7e745000-7e840000       Deferred        shell32<elf>
  \-PE  7e760000-7e840000       \               shell32
ELF     7e840000-7e8e0000       Deferred        comdlg32<elf>
  \-PE  7e850000-7e8e0000       \               comdlg32
ELF     7e8e0000-7e8f9000       Deferred        version<elf>
  \-PE  7e8f0000-7e8f9000       \               version
ELF     7e8f9000-7e90c000       Deferred        libresolv.so.2
ELF     7e90c000-7e92a000       Deferred        iphlpapi<elf>
  \-PE  7e910000-7e92a000       \               iphlpapi
ELF     7e92a000-7e957000       Deferred        ws2_32<elf>
  \-PE  7e930000-7e957000       \               ws2_32
ELF     7e957000-7e971000       Deferred        wsock32<elf>
  \-PE  7e960000-7e971000       \               wsock32
ELF     7e971000-7e987000       Deferred        glu32<elf>
  \-PE  7e980000-7e987000       \               glu32
ELF     7e987000-7e993000       Deferred        libgcc_s.so.1
ELF     7ea7d000-7ea86000       Deferred        libdrm.so.2
ELF     7ea86000-7ea8b000       Deferred        libxxf86vm.so.1
ELF     7ea8b000-7ea90000       Deferred        libxdmcp.so.6
ELF     7ea90000-7eb10000       Deferred        libglu.so.1
ELF     7eb10000-7eb70000       Deferred        libgl.so.1
ELF     7eb70000-7ec61000       Deferred        libx11.so.6
ELF     7ec61000-7ec6f000       Deferred        libxext.so.6
ELF     7ec6f000-7ecf0000       Deferred        opengl32<elf>
  \-PE  7ec90000-7ecf0000       \               opengl32
ELF     7ecf0000-7ed37000       Deferred        advapi32<elf>
  \-PE  7ed00000-7ed37000       \               advapi32
ELF     7ed37000-7edcd000       Deferred        gdi32<elf>
  \-PE  7ed50000-7edcd000       \               gdi32
ELF     7edcd000-7ef09000       Deferred        user32<elf>
  \-PE  7edf0000-7ef09000       \               user32
ELF     7ef09000-7ef98000       Deferred        winmm<elf>
  \-PE  7ef20000-7ef98000       \               winmm
ELF     7ef98000-7efa3000       Deferred        libnss_files.so.2
ELF     7efa3000-7efad000       Deferred        libnss_nis.so.2
ELF     7efad000-7efc4000       Deferred        libnsl.so.1
ELF     7efc4000-7efeb000       Deferred        libm.so.6
ELF     7efec000-7f000000       Deferred        lz32<elf>
  \-PE  7eff0000-7f000000       \               lz32
ELF     f7d11000-f7d14000       Deferred        libxinerama.so.1
ELF     f7d14000-f7d1d000       Deferred        libnss_compat.so.2
ELF     f7d1e000-f7d22000       Deferred        libdl.so.2
ELF     f7d22000-f7e63000       Deferred        libc.so.6
ELF     f7e64000-f7e7b000       Deferred        libpthread.so.0
ELF     f7e7d000-f7e80000       Deferred        libxau.so.6
ELF     f7e90000-f7fa1000       Deferred        libwine.so.1
ELF     f7fa3000-f7fc1000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
0000000e 
        0000000f    0
0000000c (D) Z:\media\win\Jeux\Prey\prey.exe
        00000014   15
        00000013   15
        00000011    0
        00000010    0
        0000000d    0 <==

```
Which is pretty bad too... Looks like the link between 64bit os and 32bit lib is not working.

wInd

---

