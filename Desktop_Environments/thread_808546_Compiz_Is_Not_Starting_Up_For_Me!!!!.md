---
title: "Compiz Is Not Starting Up For Me!!!!"
date: 2008-05-26
forum: Desktop Environments
---

### Post by JayDeePlus on 2008-05-26
i don't know........after an update......i restarted computer and compiz didn't come back on..........i mean i thought there was no on off switch with compiz...........

can someone help me?........

---

### Post by CameO73 on 2008-05-26
First, find out what is going wrong ... use the [Compiz-check script](http://ubuntuforums.org/showthread.php?t=799070).

---

### Post by JayDeePlus on 2008-05-26
> Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 


the video card?

---

### Post by JayDeePlus on 2008-05-26
ok i think it's cuz i tried installing a second video card so i can have dual screens.....but it didn't recognize the drivers and crashed my system or something.........so i toke it out and did a system recovery and was able to get back to the desktop......i guess i juss now noticed that Compiz is not on...........

it's that Nvidia card........i don't wanna use it now since i've gotten a second computer............

how can i fix this problem?.......

---

### Post by pjok on 2008-05-26
> **JayDeePlus said:**
> i don't know........after an update......i restarted computer and compiz didn't come back on..........i mean i thought there was no on off switch with compiz...........

can someone help me?........

Have you started it at all? 

terminal -> <alt>F2, then type --compiz replace

---

### Post by JayDeePlus on 2008-05-26
yea i juss tried........it tried to start up but it turned off.......i think it's something to do with the video card drivers......how do i change the settings to my video drivers?......

---

### Post by pjok on 2008-05-26
> **JayDeePlus said:**
> yea i juss tried........it tried to start up but it turned off.......i think it's something to do with the video card drivers......how do i change the settings to my video drivers?......

Depends on which graphic card you're using. However, are there displayed any error messages if you try running the "--compiz replace"-command in the terminal?

---

### Post by JayDeePlus on 2008-05-26
no......it's kinda like it starts up.....cuz like the screen flashes......and then brings back to the desktop.........

but no there is no error message......... but am i suppose to type in "--compiz replace" or "compiz replace" ...........cuz it do give me an error when i try "--compiz replace"

---

### Post by pjok on 2008-05-26
It's --compiz replace. 

Show me the error message which is printed when you type --compiz replace.

---

### Post by JayDeePlus on 2008-05-26
> 
Could not open location 'file:///home/jaydee/--compiz%20replace'
The location or file could not be found.



that don't seem right because i kno its installed.......

---

### Post by pjok on 2008-05-26
Installed, yes. But the proccess ain't running by default upon installation. Manual start of the application/proccess is by $ --compiz replace . 

When you got it up and running, functionable etc- then you can care of by setting it to start by default on startup.

---

### Post by JayDeePlus on 2008-05-26
but that code isn't loading compiz..........i mean i can get to the compiz desktop setting manager......thro system> Preferences > Advanced Desktop Settings

but i can't start it.........

---

### Post by JayDeePlus on 2008-05-26
> Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 


is this saying anything?......

---

### Post by pjok on 2008-05-26
It seems like that no drivers are used. 

Check if there are any options avalible in: System > Administration > Hardware Drivers

---

### Post by JayDeePlus on 2008-05-26
>  no proprietary drivers are in use on this system

and the box below that is empty

---

### Post by pjok on 2008-05-26
By experience I advice you to google the error message to find an awnser. 
I'm off to bed. Good Luck!

---

### Post by JayDeePlus on 2008-05-26
ok........i've done as u've said and googled the compiz check output instead of the problem............and i have found another post on the same problem in another post

[http://ubuntuforums.org/showthread.php?t=806937]("http://ubuntuforums.org/showthread.php?t=806937")

ok i've done as they have asked by running the grep -v ^# /var/log/Xorg.0.log command............

and this is what i get

> (==) intel(0): VideoRam: 131072 KB
(**) intel(0): Framebuffer compression disabled
(**) intel(0): Tiling enabled
(II) intel(0): Page Flipping disabled
(==) intel(0): Write-combining range (0xf0000000,0x8000000)
(II) intel(0): vgaHWGetIOBase: hwp->IOBase is 0x03d0, hwp->PIOOffset is 0x0000
(WW) intel(0): EXA greedy migration mode enabled.
(II) EXA(0): Forcing greedy migration option
(II) EXA(0): Offscreen pixmap area of 19660800 bytes
(II) EXA(0): Driver registered support for the following operations:
(II)         Solid
(II)         Copy
(II)         Composite (RENDER acceleration)
(==) intel(0): Backing store disabled
(==) intel(0): Silken mouse enabled
(II) intel(0): Initializing HW Cursor
(II) intel(0): xf86BindGARTMemory: bind key 0 at 0x000df000 (pgoffset 223)
(II) intel(0): xf86BindGARTMemory: bind key 1 at 0x000e0000 (pgoffset 224)
(II) intel(0): xf86BindGARTMemory: bind key 2 at 0x00720000 (pgoffset 1824)
(II) intel(0): Fixed memory allocation layout:
(II) intel(0): 0x00000000-0x0001ffff: ring buffer (128 kB)
(II) intel(0): 0x00020000-0x00024fff: HW cursors (20 kB)
(II) intel(0): 0x00025000-0x0002cfff: logical 3D context (32 kB)
(II) intel(0): 0x000df000:            end of stolen memory
(II) intel(0): 0x000df000-0x000dffff: overlay registers (4 kB, 0x0000000034594000 physical
)
(II) intel(0): 0x000e0000-0x0071ffff: front buffer (6400 kB)
(II) intel(0): 0x00720000-0x019dffff: exa offscreen (19200 kB)
(II) intel(0): 0x08000000:            end of aperture
(II) intel(0): Output configuration:
(II) intel(0):   Pipe A is on
(II) intel(0):   Display plane A is now enabled and connected to pipe A.
(II) intel(0):   Output VGA is connected to pipe A
(II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
(II) intel(0): DPMS enabled
(II) intel(0): Set up overlay video
(II) intel(0): direct rendering: Disabled
(--) RandR disabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
(II) intel(0): Setting screen physical size to 300 x 225
(WW) Configured Mouse: No Device specified, looking for one...
(II) Configured Mouse: Setting Device option to "/dev/input/mice"
(--) Configured Mouse: Device: "/dev/input/mice"
(==) Configured Mouse: Protocol: "Auto"
(**) Option "CorePointer"
(**) Configured Mouse: always reports core events
(**) Option "Device" "/dev/input/mice"
(==) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Configured Mouse: Sensitivity: 1
(**) Option "CoreKeyboard"
(**) Generic Keyboard: always reports core events
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1030"x0.0  107.00  1280 1320 1424 1664  1030 1036 1039 1071 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1030"x0.0  107.00  1280 1320 1424 1664  1030 1036 1039 1071 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1030"x0.0  107.00  1280 1320 1424 1664  1030 1036 1039 1071 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1030"x0.0  107.00  1280 1320 1424 1664  1030 1036 1039 1071 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1030"x0.0  107.00  1280 1320 1424 1664  1030 1036 1039 1071 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) 3rd Button detected: disabling emulate3Button
SetClientVersion: 0 9
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1030"x0.0  107.00  1280 1320 1424 1664  1030 1036 1039 1071 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1030"x0.0  107.00  1280 1320 1424 1664  1030 1036 1039 1071 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1030"x0.0  107.00  1280 1320 1424 1664  1030 1036 1039 1071 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1030"x0.0  107.00  1280 1320 1424 1664  1030 1036 1039 1071 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1030"x0.0  107.00  1280 1320 1424 1664  1030 1036 1039 1071 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1030"x0.0  107.00  1280 1320 1424 1664  1030 1036 1039 1071 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
SetClientVersion: 0 9
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1030"x0.0  107.00  1280 1320 1424 1664  1030 1036 1039 1071 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): Printing DDC gathered Modelines:
(II) intel(0): Modeline "1280x1030"x0.0  107.00  1280 1320 1424 1664  1030 1036 1039 1071 +hsync +vsync (64.3 kHz)
(II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
(II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
(II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
(II) intel(0): Modeline "640x480"x0.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
(II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz)
(II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
(II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
(II) intel(0): Modeline "1024x768"x0.0   44.90  1024 1032 1208 1264  768 768 776 817 interlace +hsync +vsync (35.5 kHz)
(II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
(II) intel(0): EDID vendor "PBE", prod id 29219
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
(II) intel(0): DDCModeFromDetailedTiming: Ignoring tiny 1x1 mode
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled



As the guy in the post pointed out..............on line EE it tells me the problem

> (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)


ok i kno this IS the problem.........because i tried installing a NVidia video card.........because i was wanting to have dual screens........but for some reason unix had a problem finding drivers for it or something.......and kept crashing when i tried to start up with it installed...........so i removed the card from my tower..........and now i guess it's still looking? for the NVIDIA card?.........but it's not there because i removed the card?...........so how do i "Un-Install" the NVIDIA Drivers?..........or at least can someone tell me how the guy in this post [http://ubuntuforums.org/showthread.php?t=806937]("http://ubuntuforums.org/showthread.php?t=806937"), how did he fix his problem?.........

---

### Post by CameO73 on 2008-05-27
Start up Synaptic and search for **nvidia**. Make sure none of those are installed (otherwise: rightclick any installed and select 'Mark for complete removal'). Then 'Apply' your changes and reboot.

Oh, and by the way, the right way to start Compiz is
```
compiz --replace
```This can be read as: start **compiz** with the **--replace** option (replaces your current window manager; usually Metacity). But if everything works as it should, you shouldn't have to do this manually.

---

### Post by JayDeePlus on 2008-05-27
> jaydee@jaydee-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2562 (rev 01) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "<Shift><Control><Super>" found in configuration database is not a valid value for keybinding "move_to_workspace_1"


i've been trying so hard to figure this out.....can someone help.....plzzzzzzzzzzz

---

### Post by JayDeePlus on 2008-05-28
i still need help with this..........

---

### Post by Forlong on 2008-05-28
Post the output of ```
dpkg -l | grep nvidia
``` and use the forum's [noparse]```
[/noparse] tag please (# button)


**Also, please edit your posting before, where you pasted your xorg log and change [noparse]> [/noparse] and [noparse][/noparse] to [noparse][CODE][/noparse] and [noparse]
```[/noparse] respectively.**

---

