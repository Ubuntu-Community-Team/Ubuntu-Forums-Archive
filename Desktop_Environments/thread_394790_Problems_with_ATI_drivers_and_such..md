---
title: "Problems with ATI drivers and such."
date: 2007-03-27
forum: Desktop Environments
---

### Post by The_Cleric on 2007-03-27
Hi Guys,

Im new... 
I am having issues. 

fglrxinfo spits this out.

[I]Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (1.5 Mesa 6.5.2)
[/I]

I am trying to get Beryl to work. I have tryed every guide there is. I have been instructed to reinstall everything and even change the "Driver" line to "radeon" (still not sure what that will fix...

Any how. I believe there is a problem somewhere. My issue is with the Xlib: line. It says its looking for XFree86-DRI. 

(Output of xorg.conf)
[I]
Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Option          "AGPFastWrite" "yes"
        Option          "AGPMode" "4"
        Option          "ColorTiling" "on"
        Option          "EnablePageFlip" "true"
        Option          "AccelMethod" "EXA"
        Option          "XAANoOffScreenPixMaps"
        Option          "RenderAccel" "true"
        Option          "DRI" "true"
        BusID           "PCI:1:0:0"
EndSection

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "on"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
[/I]

I still have not been able to get beryl to load. The manager loads, and thats a plus. 

Here is the output of lspci just incase:
[I]01:00.0 VGA compatible controller: ATI Technologies Inc RV530LE [Radeon X1600]
01:00.1 Display controller: ATI Technologies Inc Unknown device 71e6[/I]

Any help in getting Beryl to work would be greatful. Any help in getting my device drivers to work correctly would be awsom! 

thanks,
The Cleric

P.S.
Can someone point me in the direction of getting more than 1024x768 out of my card?

---

### Post by pappo on 2007-03-27
The line:  Xlib: extension "XFree86-DRI" missing on display ":0.0", usually means you need to re-install your drivers.   Here are some Google links when I searched using that error line:

[http://www.linuxquestions.org/questions/showthread.php?t=277294](http://www.linuxquestions.org/questions/showthread.php?t=277294)
[http://www.linuxforums.org/forum/peripherals-hardware/36000-xlib-extension-xfree86-dri-missing-display-0-0-a.html](http://www.linuxforums.org/forum/peripherals-hardware/36000-xlib-extension-xfree86-dri-missing-display-0-0-a.html)


To get more than 1024x768 all you need to do is add the resolution you want to your /etc/X11/xorg.conf file.

MAKE SURE YOU MAKE A COPY OF THE ORIGINAL xorg.conf file first, by doing the following:
  "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original     Then if it messes up, all you have to do is go back into a terminal and do  " sudo /etc/X11/xorg.original /etc/X11/xorg.conf and you will be back to where you started.

Here is what I did in my xorg.conf file to add 1600x1200 resolution.
I just removed all the modes except my "Depth 24" which is my default depth and added "1600x1200" in front.
It worked for me.
Here is a copy of the Screen section of my xorg.conf file.  
-----------------------------------------------------------------------------------------------------
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. R420 JP [Radeon X800XT]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1600x1200" "1024x768" "800x600" "640x480"
        EndSubSection
-------------------------------------------------------------------------------------------------------

---

