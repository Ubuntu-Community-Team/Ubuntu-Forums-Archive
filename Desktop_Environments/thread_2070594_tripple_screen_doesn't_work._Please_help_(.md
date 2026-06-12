---
title: "tripple screen doesn't work. Please help :("
date: 2012-10-13
forum: Desktop Environments
---

### Post by bosil on 2012-10-13
Hello everybody,

I just installed xubuntu 12.04 (64bit amd build) on my desktop. But I have a problem with my monitors. I have three monitors on two graphic cards. I have an amd 4870 (with 2 monitors) and an onboard HD 4200 with one monitor. I want to create one large desktop with them (like I had on windows) so I can drag-and-drop screens between them. 

First I tried it with the open source driver. But I could only detect the screens from my HD 4870 :'( (I'm a linux noob :s ). Whenn I saw I couldn't get it to work. I installed the closed source  fglrx (NOT the post update version, but the normal). Now I'm able to get my three monitors work :). But only the 2 monitors on my HD 4870 can I use to 'extend desktop'. So I can only drag-and-drop screens between those 2.On the third monitor on my HD 4200 I can go with my cursor on it, but I can't drag a 'window' to that third screen.

Than I wanted to configure xinerama because it would let me use the drag-and-drop function on my third screen. But I can't configure xinerama because it says:
xinerama cannot be enabled because the combined desktop area is too large. I found more of these xinerama transparant errors. ([http://www.youtube.com/watch?v=3b_UkPwLZCM](http://www.youtube.com/watch?v=3b_UkPwLZCM)) also my avant window navigator dock wasn't working.

So I want to use my three screens, so I can move windows from screen 1 to screen 3 to screen 2 etc.

I don't really know how I can do it. And I don't really care if it can be done with the opensource driver or the closed source driver.

Please help.

Thanks in advance.


so looks my xorg.conf file right now:
> Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[2]-0" 0 0
    Screen         "amdcccle-Screen[1]-0" 3200 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "ServerFlags"
    Option        "Xinerama" "off"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1920x1080"
    Option        "TargetRefresh" "60"
    Option        "Position" "1280 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-Default monitor"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "480x640"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" ""
    Option        "Disable" "false"
EndSection

Section "Monitor"
    Identifier   "1-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1280x1024"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[2]-0"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
    Option        "Monitor-DFP1" "0-DFP1"
    BusID       "PCI:2:0:0"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[2]-1"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:2:0:0"
    Screen      1
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-CRT1" "1-CRT1"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[2]-0"
    Device     "amdcccle-Device[2]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   3200 3200
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[2]-1"
    Device     "amdcccle-Device[2]-1"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSectionbut I'm not able to drag windows between the screens from my HD4870 to my hd 4200 :(


edit1: :o I could made it work by just changing the line "Option        "Xinerama" "off" to Option        "Xinerama" "on" :o. Now I can drag and drop between my 3 displays but I don't know if that's the right solution XD. But now my left screen (the 1280x1024 on my HD 4870 is my main screen, and I want my 1920x1080 screen on my HD 4870 to be my main screen, somebody knows how to change?

edit2: I don't know if this is a bug, but I'm using closed source ati drivers and when I enable xinerama, I'm no longer able to make the xfce top-panel from my xubuntu transparant, all the filters are gone (alpha , transparancy,leave...). Maybe I can set it manually, but I don't know where.

---

