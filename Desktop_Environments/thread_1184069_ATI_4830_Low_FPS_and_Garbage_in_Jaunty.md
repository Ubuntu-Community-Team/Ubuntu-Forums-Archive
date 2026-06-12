---
title: "ATI 4830 Low FPS and Garbage in Jaunty"
date: 2009-06-10
forum: Desktop Environments
---

### Post by 2bmuni on 2009-06-10
Hi,

I am using the ATI drivers 9.5 for HD4830, the screen fonts look blurry and I get strange pixelation at the bottom of the right corner. 

These are some of the stats and Xorg.conf file

name of display: :0.0
display: :0  screen: 0
direct rendering: Yes 
server glx vendor string: ATI
server glx version string: 1.4
ati

glxgears
Running synchronized to the vertical refresh.  The framerate should be
approximately 1/58248 the monitor refresh rate.
380 frames in 5.0 seconds = 75.941 FPS
376 frames in 5.0 seconds = 75.027 FPS
376 frames in 5.0 seconds = 74.961 FPS
375 frames in 5.0 seconds = 75.000 FPS

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"                              
EndSection                                                     

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth    24                 
        SubSection "Display"               
                Viewport   0 0             
                Virtual   2560 1024        
                Depth     24               
        EndSubSection                      
EndSection                                 

Section "Module"
        Load  "glx"
EndSection         

Section "DRI"
        Group        "Video"
        Mode         0666   
EndSection                  

Section "Extensions"
        Option      "RENDER" "Enable"
        Option      "DAMAGE" "Enable"
        Option      "Composite" "Enable"
EndSection

Section "ServerLayout"
        Identifier     "aticonfig Layout"
        Screen      0  "aticonfig-Screen[0]-0" 0 0
        Option      "AIGLX" "on"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Option      "XAANoOffscreenPixmaps" "on"
        Option      "TexturedVideo" "on"
        Option      "VideoOverlay" "off"
        Option      "OpenGLOverlay" "off"
        Option      "Textured2D" "on"
        Option      "UseFastTLS" "1"
        Option      "BackingStore" "on"
        BusID       "PCI:4:0:0"
        Driver  "fglrx"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "off"
        Option      "DontZap" "False"
EndSection

---

