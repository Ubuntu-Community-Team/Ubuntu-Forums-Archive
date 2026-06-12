---
title: "Weird problems KDM"
date: 2007-01-22
forum: Desktop Environments
---

### Post by tsvim on 2007-01-22
Hi I've been having trouble with kdm starting up, it does start up but the time it takes is impossible.
I tried manually editing my xorg.conf file. But alas, to no avail.
Also when I get the KDM screen I get the picture in 256 colours, if I do a Alt-E (Restart Xserver) I get the colours all right. (If I don't restart the xserver I get the same res on the desktop - very ugly). 
On another note, although these might be related. When I open a Konqueror window it opens up nice and well, but when I try to click on an icon it takes forever till it opens up the folder/file I clicked on. (Note: if I enter the name in the address bar, or right click on the file/folder and request to open it in a new tab, it works perfectly fine.

Please help me make Ubuntu my favorite distro again, cause if I don't get a solution for these problems within the next month, I'll have to move to something usable, and I really don't want to do that (Ubuntu has been my first true love with Linux) (Quad booting my machine: SUSE, (K)Ubuntu, Fedora, M$ XP).

Specs: using Kubuntu 6.10 amd64 version on Dell Inspiron e1405 with 915resolution patch to get widescreen 1440*900.

Attaching my xorg.conf file:

> Section "Files"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
        Load    "dbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us,il"
        Option          "XkbVariant"    ",si1452"
        Option          "XkbOptions"    "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Intel i945GM"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        131072          # 128 MB
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel i945GM"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           16
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option  "Composite"     "Enable"
EndSection


Note I tried thinkering before with beryl/aiglx but as it caused even more trouble I stopped. first let's get this working, then we canstart playing games.

T.
Registered Linux User: #440184

---

### Post by tsvim on 2007-01-23
Ok, figures one solution to multiple problems:
adding "notsc nmi_watchdog=0" to the boot entry, as well as blacklisting the video module by adding it to /etc/modprob.d/blacklist (Add entry blacklist video) solves the following problems on my Dell (some I wasn't even aware of):
[LIST]
[*]Loading KDM at a normal speed
[*]Working brightness buttons
[*]Konqueror doesn't act funny anymore
[*]Apparantly (didn't check) this should also allow for shutting down the lid and plugging in the power cord without causing problems. (I'll post it once I check it out)
[/LIST]

Note: still a problem is the xserver starting in 256 colors.

---

### Post by unimatrix on 2007-02-20
Hello.

I too am experiencing a similar problem of broken colors on startup with KDM. It happens a few moments after the login screen loads (for about 2 seconds it's fine at first). Though I don't think it's 256 colors, at least in my case. It might aswell be 16k... I'm not very good with recognizing that from a picture.
This didn't happen when I was using GDM. Only after I switched to kdm which I have done like this: 
[http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/](http://www.howtogeek.com/howto/ubuntu/how-to-switch-between-gdm-and-kdm-on-ubuntu/)

The funny thing is 256colors appear
A simple Ctrl+Alt+Backspace solves the problem, which is weird. I don't see why something should be different...
Well, anyway, I'll post if I find some kind of a solution. But if someone has some kind of an idea I'd be happy to hear it.

---

### Post by unimatrix on 2007-03-22
I think I've finaly fixed it!

I had some weird options in the Screen section of xorg.conf, so i've comented that out. When I restarted the computer, the colors were back to normal. See if your config contains "TripleBuffer" or "backingstore". I haven't yet tried which one causes the problem, but one of them does.

> 
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "DPMS"
#    Option         "TripleBuffer" "true"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "true"
#    Option         "backingstore" "true"
    Option         "AllowGLXWithComposite" "true"


---

