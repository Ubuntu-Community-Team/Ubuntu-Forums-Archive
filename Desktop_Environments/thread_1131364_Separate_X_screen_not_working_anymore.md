---
title: "Separate X screen not working anymore"
date: 2009-04-20
forum: Desktop Environments
---

### Post by linuxfoo on 2009-04-20
Hello,
I've been using two separate X screens (not Xinerama/Twinview/whatever) for years now in KDE 3.5. I've a primary screen through DVI with a monitor attached to it (1280 x 1024) and a Full HD TV through VGA (1920 × 1080). 
I use it basically to watch videos, movies etc., so I don't care about a desktop environment there. 

Relevant parts of xorg.conf
```


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
#    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"  
    InputDevice    "Mouse0" "CorePointer"      
EndSection                                     

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection                       


Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"                         
    VendorName     "Unknown"                          
    ModelName      "Samsung SyncMaster"               
    HorizSync       30.0 - 81.0                       
    VertRefresh     56.0 - 75.0                       
    Option         "DPMS"                             
EndSection                                            

Section "Monitor"
    # HorizSync source: unknown, VertRefresh source: unknown
    Identifier     "Monitor1"                               
    VendorName     "Unknown"                                
    ModelName      "SAMSUNG"                                
    HorizSync       0.0 - 0.0                               
    VertRefresh     0.0                                     
    Option         "DPMS"                                   
EndSection                                                  

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia" 
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"      
    BusID          "PCI:1:0:0"         
    Screen          0                  
EndSection                             

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 6200"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: 1280x1024 +0+0; DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "CRT: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

But now I upgraded to KDE 4 which yielded me to serious issues with this setup. It's not working anymore. I know, KDE 4 doesn't support two separate X sessions anymore **!"§)=(!§)!"/$/"$)!/$!**. 

I get nothing but an empty X11 session on the TV. I can live with that, as I said I don't care about an desktop environment there, all I want to do is to start any given X11 program there (which should be possible anyway by using *"DISPLAY=0.1 xclock"*, shouldn't it?)

My problem is the other, the primary, screen. As soon as I start my X with 
```

Screen      1  "Screen1" RightOf "Screen0"

```

KDE gets confused, the menubar disappears (or whatever KDE 4's kicker is called) an/or out of scope of the X11 resolution from 1280x1024 (indeed I guess the menu is just below, since KDE seems virtually change the screen size, not the resolution to 1280x1080). 

So my questions are:

[list]
[*] Is there a way to start separate X sessions in KDE 4 in a KDE 3.5 manner anyway? 
[*] Is it possible to force KDE to ignore the second screen (e.g. no to know about it anyway)
[*] Has someone an idea to fix the display problems of the main screen where KDE/kwin lives?
[/list]

---

### Post by linuxfoo on 2009-04-21
No ideas?

---

### Post by jirikraus on 2009-04-28
I have the same problem if somebody has resolved that issue, please report the solution here. TwinView with the nvidia drivers is working, but that is not what i want.

---

### Post by jirikraus on 2009-04-28
This KDE4 Bug explains the problem
[http://bugs.kde.org/show_bug.cgi?id=152676](http://bugs.kde.org/show_bug.cgi?id=152676)

---

