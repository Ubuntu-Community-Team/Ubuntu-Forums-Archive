---
title: "Dual 1600sw each with Number 9 Revolution IV PCI cards Ubuntu 10.10 - single works"
date: 2011-04-22
forum: Desktop Environments
---

### Post by hyst on 2011-04-22
Below is copy & paste from my post over at linuxquestions, to which no one responded :).  I realize this is uncommon old hardware and I will probably not get a response here either, but I'd like to give it a shot before completely giving up.  Couple additional things I want to note, multiple cards and 1600SW monitors does work fine in Windows XP.  Also, I just tried nomodeset to disable KMS and it did not fix the problem.
**I had to zip up the log files to get them to attach, they are over the max 19kb size for text attachments.  I zipped em on a Mac, they are also available as text on linuxquestions but you have to be logged in to view attachments.  Sorry about all this for anyone that might actually wanna look at them.
[http://www.linuxquestions.org/questions/linux-desktop-74/dual-1600sw-each-with-number-9-revolution-iv-pci-cards-ubuntu-10-10-single-works-871828/](http://www.linuxquestions.org/questions/linux-desktop-74/dual-1600sw-each-with-number-9-revolution-iv-pci-cards-ubuntu-10-10-single-works-871828/)


Specifically for this purpose, I setup an old Athlon64 board with 2 Number Nine Revolution IV PCI cards connected to 2 SGI 1600sw monitors, and did a fresh install of Ubuntu 10.10 .  Using customized config information found online I easily got one 1600sw working at the correct 1600x1024 resolution.  Then, I went on to try to get both working, and have not been able to.  Oh, I should mention that I tried with combinations of 3 different PCI cards and 3 different 1600sw monitors, in case one of them was faulty in some strange way.  Nothing ever worked.  I apologize for the huge amount of log text here.  I had worked on trimming it down to only what I thought was relevant, but then I thought that since I am not an expert in doing so I might remove something important, so I left them complete.
***OK, logs are way too long, I'll have to figure something out :).

I've tried many different options, modules on/off, disables, Xinerama on/off, but every time I try to run with both monitors, both of their LEDs turn green (indicating a signal) but the screens stay black and X/gdm goes into a totally frozen state, I cannot force kill it (yes I am a Jedi), restart it, anything.  The system itself is not frozen, I can still do things via SSH, like look at the logs and such, but to have another try with X I have to reboot.  Examining the logs nothing jumps out at me, but I am no expert.  I did enable the extra debug info in the i128 driver, but the meaning of that output is totally beyond me.  Something that might be useful to know, I am able to use the same xorg.conf file for both working and non-working attempts, by merely commenting out the ServerLayout line that adds the second screen.  I also tried with 1 and 2 "Monitor" sections.

There are a few differences in the logs from single/working to the dual/not-working.  One difference easily spotted involves EDID info, for some reason on single display the EDID info is "(nil)" whereas with dual displays the second display, and ONLY the second display, successfully returns EDID info.  After reading that EDID data, that second monitor is stated in the log as "Found FlatPanel via DDC2…Digital flat panel forced", while the other simply says "Digital flat panel detected".  I have no idea if that is related to the lockup problem, but it's a difference that I spotted quickly.  I tried to find options for disabling DDC or EDID lookup, but everything I found said that it was specific to certain drivers, and/or it seemed to be impossible to disable.  Another small difference, when running both displays the log shows "Using SilverHammer programmable clock (MCLK 70.000 MHz)" for one and "Using SilverHammer programmable clock (MCLK 77.344 MHz)" for the other.

There is an MTRR error that appears in console output and system logs, "error setting MTRR (base = 0xd0000000, size = 0x02000000, type = 1) Invalid argument (22)".  At one point I thought the MTRR error was something related, but it happens whether I launch the working config or not, it just occurs twice when I try to run both displays.

The log for all my failed dual display attempts always ends with the line:
"(II) GLX: Initialized DRISWRAST GL provider for screen 1"
When running the working single display, the log always continues from there after which it appears to be only configuring items related to input devices, 'power button', keyboard, etc.

These video cards have also have a VGA output, so to see if it was something specific to the 1600sw I tried one 1600sw and one other regular LCD, via VGA.  I got the same result, both black screens and X completely frozen.  On the VGA LCD I was able to get the signal info and it shows 800x600 H:38 V:60.  I doubt it will be at all relevant but it's something I tried.

Just as guess here, but I wonder if this might have something to do with powersaving features of the monitor, and that somehow being triggered/stuck in some unusual way when launching with dual displays.  The reason I mention this is that when it happens, the screen looks similar to when the monitor goes into standby in text/console mode.  The light stays green and the monitor backlighting is on.  The only problem with this theory is it does not explain why X hangs and cannot be restarted, killed, etc.

Well, I've tried to include as much information as I could, sorry for such a long post.  Below is the config file, had to attach the logs, sorry.  During testing I tried different methods of launching X, so the end of the working log isn't really important.  At some points I tried to get more information using gdb, but I found debugging X very difficult as I couldn't determine how to properly launch it via SSH so that gdb would be attached to the actual final Xorg program.  There are so many intermediate steps, scripts, etc. in the way, I was never able to get an actual working Xorg launch to test and run gdb with.  I will continue researching that option.

xorg.conf, note again that this file works by merely commenting out second screen in ServerLayout:
> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)

Section "Device"
        Identifier "N9R4-1"
        Driver "i128"
        Option "Debug" "on"
        BusID "PCI:5:6:0"
EndSection

Section "Device"
        Identifier "N9R4-2"
        Driver "i128"
        Option "Debug" "on"
        BusID "PCI:5:7:0"
EndSection

Section "Modes"
        Identifier "modes-1600sw"
        #[http://www.x.org/releases/X11R7.5/doc/I128.html](http://www.x.org/releases/X11R7.5/doc/I128.html)
        Modeline "1600x1024d32" 103.125 1600 1600 1656 1664 1024 1024 1029 1030 HSkew 7 +Hsync +Vsync
        Modeline "1600x1024d16" 103.125 1600 1600 1656 1664 1024 1024 1029 1030 HSkew 5 +Hsync +Vsync
        Modeline "1600x1024d08" 103.125 1600 1600 1656 1664 1024 1024 1029 1030 HSkew 1 +Hsync +Vsync
        Modeline "800x512d32" 54.375 800 800 840 848 512 512 514 515 HSkew 7 DoubleScan +Hsync +Vsync
        Modeline "800x512d16" 54.375 800 800 840 848 512 512 514 515 HSkew 5 DoubleScan +Hsync +Vsync
        Modeline "800x512d08" 54.375 800 800 840 848 512 512 514 515 HSkew 1 DoubleScan +Hsync +Vsync
EndSection

Section "Monitor"
        Identifier "1600sw-1"
        VendorName "Silicon Graphics"
        ModelName "1600SW"
        HorizSync 27.0-96.0 # kHz
        VertRefresh 29-31, 50.0-80.0, 119-124 # Hz
        Option "DPMS"
        UseModes "modes-1600sw"
EndSection

Section "Monitor"
        Identifier "1600sw-2"
        VendorName "Silicon Graphics"
        ModelName "1600SW"
        HorizSync 27.0-96.0 # kHz
        VertRefresh 29-31, 50.0-80.0, 119-124 # Hz
        Option "DPMS"
        UseModes "modes-1600sw"
EndSection

Section "Screen"
        Identifier "1"
        Device "N9R4-1"
        Monitor "1600sw-1"
        DefaultDepth 24
        SubSection "Display"
                Depth 24
                Modes "1600x1024d32" "800x512d32"
        EndSubSection
EndSection

Section "Screen"
        Identifier "2"
        Device "N9R4-2"
        Monitor "1600sw-2"
        DefaultDepth 24
        SubSection "Display"
                Depth 24
                Modes "1600x1024d32" "800x512d32"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier "Default Layout"
        Screen 0 "1" 0 0
        Screen 1 "2" RightOf "1"
        #Option        "Xinerama" "On"                                                        
        #InputDevice "Generic Keyboard"
        #InputDevice "Configured Mouse"
EndSection

Section "DRI"
        Mode 0666
EndSection


---

### Post by Blueshell on 2011-07-29
Did you ever figure this out?  I'm about to be in exactly your situation---I have a pair of 1600SW's with the Rev #9 cards, currently working perfectly using Xinerama in 5.04 (yes, that's 5.04).  I haven't dared rev the OS in years precisely because I figured it'd be a bear to get these working again, but running other machines headless and displaying on the old one is starting to get, well, old...  [If you like, I could throw you my current configuration, though remember, it's for an X server etc that's 4-5 years old...]
Thanks!

---

