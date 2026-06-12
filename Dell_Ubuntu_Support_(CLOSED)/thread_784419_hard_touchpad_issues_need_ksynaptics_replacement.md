---
title: "hard touchpad issues need ksynaptics replacement"
date: 2008-05-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by ihavenoname on 2008-05-06
I'm on a dell inspiron 640m
my touch pad is exhibiting really sensative behavior. By that I mean while I am typing my touch pad will click on something else and change the focus away from the place where I am typing. This is a common thing with most linux things, however usually I can deal with it using ksynaptics or something like that. However ksynaptics is not in the repos and gstnaptics doesn't work.  Any ideas?

---

### Post by Tiede on 2008-05-06
Try using the new mouse locking feature in Hardy.
Right-click an a panel, select add to panel, and select the mouse grabbing tool. (my sysyem is in french, so the name might change...) There should be a mouse icon next to it.
whenever you are typing a doc, just click on the green area. It'll turn red and 'grab' your mouse until you click again.

You probably are experiencing this because your arm and/or palm is passing on the touchpad surface. That is why the grabber is cool.

---

### Post by ihavenoname on 2008-05-06
> **Tiede said:**
> Try using the new mouse locking feature in Hardy.
Right-click an a panel, select add to panel, and select the mouse grabbing tool. (my sysyem is in french, so the name might change...) There should be a mouse icon next to it.
whenever you are typing a doc, just click on the green area. It'll turn red and 'grab' your mouse until you click again.

You probably are experiencing this because your arm and/or palm is passing on the touchpad surface. That is why the grabber is cool.

I'm on KDE, so I don't think this applies. Thanks for the info though.

---

### Post by Tiede on 2008-05-06
oops! my bad. Unfortunately. I don't spend that much time on KDE to know what an alternative would be. Anyone else to the rescue? :)

---

### Post by Orion2000za on 2008-05-20
> **ihavenoname said:**
> I'm on KDE, so I don't think this applies. Thanks for the info though.

If you go look for qsynaptics homepage you will find that the developer has discontinued both q- and ksynaptics. Instead he has put together a "hack" (his words) called Touchfreeze that is supposed to basically just delay the reaction from the touchpad. Should work in either KDE and Gnome. 

Have just installed it but not really tried it out yet.

---

### Post by Shane10101 on 2008-05-20
I have touchfreeze running, but it doesn't seem to be doing anything.  It doesn't look like there's an entry for the touchpad in my xorg.conf, though.  I'm guessing this is the problem, but I'm not sure how to fix it!  Could someone give me a hand?  

I'm using an Averatec 3715.  My Logitec mouse is showing up in the hardware configuration (hardDrake), & my current xorg.conf follows:

Section "Extensions"
    Option "Composite"
EndSection

Section "ServerFlags"
    #DontZap # disable <Crtl><Alt><BS> (server abort)
    #DontZoom # disable <Crtl><Alt><KP_+>/<KP_-> (resolution switching)
    AllowMouseOpenFail # allows the server to start up even if the mouse does not work
EndSection

Section "Module"
    Load "dbe" # Double-Buffering Extension
    Load "v4l" # Video for Linux
    Load "extmod"
    Load "type1"
    Load "freetype"
    Load "glx" # 3D layer
EndSection

Section "InputDevice"
    Identifier "Keyboard1"
    Driver "kbd"
    Option "XkbModel" "pc105"
    Option "XkbLayout" "us"
    Option "XkbOptions" "compose:rwin"
EndSection

[B]Section "InputDevice"
    Identifier "Mouse1"
    Driver "mouse"
    Option "Protocol" "ExplorerPS/2"
    Option "Device" "/dev/mouse"
EndSection[/B]

Section "Monitor"
    Identifier "monitor1"
    VendorName "Generic"
    ModelName "Flat Panel 1024x768"
    HorizSync 31.5-55
    VertRefresh 40-70
    
    # TV fullscreen mode or DVD fullscreen output.
    # 768x576 @ 79 Hz, 50 kHz hsync
    ModeLine "768x576"     50.00  768  832  846 1000   576  590  595  630
    
    # 768x576 @ 100 Hz, 61.6 kHz hsync
    ModeLine "768x576"     63.07  768  800  960 1024   576  578  590  616
EndSection

Section "Device"
    Identifier "device1"
    VendorName "VIA Technologies Inc."
    BoardName "OpenChrome"
    Driver "openchrome"
    Option "DPMS"
EndSection

Section "Screen"
    Identifier "screen1"
    Device "device1"
    Monitor "monitor1"
    DefaultColorDepth 24
  
[snip]
    
    Subsection "Display"
        Depth 24
        Modes "1024x768" "832x624" "800x600" "640x480" "480x360" "320x240"
    EndSubsection
EndSection

Section "ServerLayout"
    Identifier "layout1"
    InputDevice "Keyboard1" "CoreKeyboard"
    InputDevice "Mouse1" "CorePointer"
    Screen "screen1"
EndSection

---

