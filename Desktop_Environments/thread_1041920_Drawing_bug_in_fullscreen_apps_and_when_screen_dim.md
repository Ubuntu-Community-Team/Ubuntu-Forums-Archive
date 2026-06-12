---
title: "Drawing bug in fullscreen apps and when screen dims"
date: 2009-01-17
forum: Desktop Environments
---

### Post by steampoweredlawngnome on 2009-01-17
Hello all,

I always seem to end up with the oddball problems, but maybe someone has seen and/or knows how to fix this;

When I'm using a full screen app, like Gwenview in fullscreen mode, or a sudo prompt comes up, Kwin starts drawing boxes around everything it animates, e.g. window buttons changing color = black box drawn around each one, OK button getting highlighted = black box drawn around it, etc.

[IMG]http://i651.photobucket.com/albums/uu238/steampoweredlawngnome/artifacts1.png?t=1232180144[/IMG] ([http://s651.photobucket.com/albums/uu238/steampoweredlawngnome/?action=view&current=artifacts1.png](http://s651.photobucket.com/albums/uu238/steampoweredlawngnome/?action=view&current=artifacts1.png))

I can make the boxes go away if I turn off direct rendering, but then KWin performs like crap and everything is choppy and unpleasant. Direct rendering makes KWin butter-smooth, but for those insidious boxes. I have also experimented with vsync, each different texture filter and OpenGL mode, and various nVidia settings. 

Does anybody have a trick up their sleeve for getting rid of the boxes, that does not involve turning off compositing/direct rendering, or using Compiz? I'm using an nVidia 7900GTX with the 180.22 driver and KDE 4.2RC1, though the problem has been happening since at least KDE 4.1.0 and nvidia driver 167.xx.


Any help would be greatly appreciated, Thanks! 


xorg.conf;
----------------------------------------
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
    Option	   "UseEvents" "on"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by adam_kimber on 2009-01-17
You seem to have my problem. I had some weird bugs that I could not solve and a reinstall did not work either. I realised that as i reuse my home directory every install it might be something to do with that. So i moved all the . files in the home to a backup folder using the live cd, deleted the partition which had root on and reinstalled. So far no bugs! 

So as a last ditch resort you could use the above method. 

Also it sounds like you have a permissions issue. Create a new user, if they had have the same problem, then its a base config bug of some sorts. However if they don't then its a user config issue. 

I am sorry that I do not have the answer. :( Its a process of elimination. 

PS can you post the output of dmseg as it might be something i have overlooked.....

---

### Post by steampoweredlawngnome on 2009-01-17
dmesg appears to have TCP/IP messages (sample below):

[26768.919915] Inbound IN=eth0 OUT= MAC=XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX:XX SRC=XX.XXX.XXX.XXX DST=XX.XXX.XXX.XXX LEN=60 TOS=0x00 PREC=0x00 TTL=40 ID=18852 DF PROTO=TCP SPT=50533 DPT=6881 WINDOW=5840 RES=0x00 SYN URGP=0

It's just thousands of entries nearly identical to the above (mac and IP #'s censored). I triggered the anomaly immediately before running dmesg to be sure.

I'm quite sure it is not a permissions issue, as it transcends this installation, and affects not only two Kubuntu installations, but also my Debian Lenny, Fedora 10, Mandriva 2009 and OpenSuSe 11.1 installs, each using their own home directory created fresh from install. I actually tried exactly your suggestion the first time about two months ago, then tried different distros. Each is installed on this machine on its own 20 GB partition, except for my primary Kubuntu installation, which has a 1TB home folder on a separate drive. I'm fairly certain it's an issue of my gfx drivers and KDE interacting poorly. 

I believe (but don't want to hear) that the problem will be resolved when either A)Qt 4.5 comes out, relying less on XRender, or B)NVidia gets their act together and fixes their drivers for Linux. :( Being the stubborn codswallop that I am, I'm still trying to find a solution anyway...

Thanks for your suggestions though, I appreciate the reply :)

---

