---
title: "Xgl annoyances"
date: 2006-09-12
forum: Desktop Environments
---

### Post by Vinze on 2006-09-12
Hey, I finally managed to get XGL to work, but there are a few annoyances. The most annoying one is that it only uses 800x600 px while my resolution is 1024x768, which is very annoying. I've put this in an image, I could only take a screenshot of the 800x600 part but I put the blueish background behind it myself, so it's probably not exactly the same shade of blue. See attachment for details.

The other one is that my windows have no borders, so if I want to close them I need some extra clicks, same goes for maximising ;)

Any help would be greatly appreciated.

---

### Post by Vinze on 2006-09-12
Oh, btw, could the window borders be theming issues?

---

### Post by bulldog on 2006-09-12
I don't know which tutorial you did follow,but I can tell you that Xgl is awsome.

Look for your resolution in your xorg.list and set it to the desired resolution and be sure that the colordept is set to 24.

Then install cgwd cgwd-themes and cgwd-themes-extra for your borders.
If you didn't do so install csm as well.

With cgwd you have the opportunity to select a nice border and with csm you can manage the xgl-plugins.

Be sure to have the latest updates installed.

Put this to your sources.list.

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

Remove what ever you use to start compiz from your session menu and put in '/usr/bin/compiz-start'

Log out and login again and it should work.

---

### Post by Vinze on 2006-09-12
> **bulldog said:**
> I don't know which tutorial you did follow,but I can tell you that Xgl is awsome.

Look for your resolution in your xorg.list and set it to the desired resolution and be sure that the colordept is set to 24.

Then install cgwd cgwd-themes and cgwd-themes-extra for your borders.
If you didn't do so install csm as well.

With cgwd you have the opportunity to select a nice border and with csm you can manage the xgl-plugins.

Be sure to have the latest updates installed.

Put this to your sources.list.

deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) dapper main
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) dapper main

Remove what ever you use to start compiz from your session menu and put in '/usr/bin/compiz-start'

Log out and login again and it should work.

I already had csm, I installed the others, I hope they'll work. Why should I add all those repositories, don't they offer all the same?

And I don't know where xorg.list is located but I guess you mean xorg.conf:

> 
(...)

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "NoLogo"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

(...)

I don't know why I have so many Display sections but at least they all got the correct resolution among them. Oh wait, they have different colour depths. But 24 is among them, I don't know how to make sure it uses it...

---

### Post by bulldog on 2006-09-12
Yes you're right,ofcourse it is xorg.conf.:) 

Did you install the drivers for your video-card?
This is how my device section looks,

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800 Ultra]"
    Driver         "nvidia"
     BusID         "PCI:1:0:0"
     Option        "NoLogo" # This option disable the startup logo. optional.
     Option        "RenderAccel"   "true"
     Option        "Triplebuffer"  "true"
     Option        "AllowXGLWithComposite" "true"
EndSection

---

### Post by Vinze on 2006-09-12
> **bulldog said:**
> Yes you're right,ofcourse it is xorg.conf.:) 

Did you install the drivers for your video-card?
This is how my device section looks,

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800 Ultra]"
    Driver         "nvidia"
     BusID         "PCI:1:0:0"
     Option        "NoLogo" # This option disable the startup logo. optional.
     Option        "RenderAccel"   "true"
     Option        "Triplebuffer"  "true"
     Option        "AllowXGLWithComposite" "true"
EndSection

I have the Nvidia drivers installed, though I don't have your last three options. They seem irrelevant to the screen size though.

The window borders are fixed, thanks, now I only need to fix the windows size and it's perfect :D

---

### Post by bulldog on 2006-09-12
That's way I asked you for the drivers.

In preferences--> screenresolution you have an option to change your screen.
Try that,maybe it's simple as that.

---

### Post by Vinze on 2006-09-12
> **bulldog said:**
> That's way I asked you for the drivers.

In preferences--> screenresolution you have an option to change your screen.
Try that,maybe it's simple as that.

I use Xubuntu, but still changing my screen resolution does not work, everything is just way larger in the same small area... ](*,)

---

### Post by bulldog on 2006-09-12
Im out of options :( 

It should be in your xorg.conf.

When you make a backup from your xorg.conf and try 

sudo dpkg -reconfigure -phigh xserver-xorg

Do this in console to see if you get the right resolution.
Afterwards you can make the changes to your xorg.conf for xgl.

{Why is there Generic Video Card in your xorg.conf and not nVidia***?}

---

### Post by Vinze on 2006-09-13
> **bulldog said:**
> Im out of options :( 

It should be in your xorg.conf.

When you make a backup from your xorg.conf and try 

sudo dpkg -reconfigure -phigh xserver-xorg

Do this in console to see if you get the right resolution.
Afterwards you can make the changes to your xorg.conf for xgl.

{Why is there Generic Video Card in your xorg.conf and not nVidia***?}

This is what I get:

> $ sudo dpkg -reconfigure -phigh xserver-xorg
Password:
dpkg: conflicting actions --control and --remove

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].
Options marked [*] produce a lot of output - pipe it through `less' or `more'

I guess there needs to be another command instead of dpkg, right?

Here's a copy of my xorg.conf, there is nvidia in there:
> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon May 15 13:23:42 PDT 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

        # paths to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/CID"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"

#	Load	"GLcore"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
#	Load	"dri"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "Emulate3Buttons" "true"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    DisplaySize     323    235
    HorizSync       28.0 - 51.0
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
    Option         "NoLogo"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

#Section "Extensions"
#    Option         "Composite" "Enable"
#EndSection



---

### Post by bulldog on 2006-09-13
X-server:                                                   
sudo dpkg-reconfigure -phigh  xserver-xorg
Renew your X-server.

I think i set a space wrong.](*,) 

Do this not in a terminal but in a console.[CTRL ALT F4]

There are some faults in you present xorg.conf.
Load "glx" set twice
Option Enable composite is disabled by #  remove the # at the end of your file.

I see in your Section monitor

Section "Monitor"
Identifier "Generic Monitor"
DisplaySize 323 235
HorizSync 28.0 - 51.0
VertRefresh 43.0 - 60.0
Option "DPMS"
EndSection

some settings I never had. 
About display size HorizSync and VertRefreh.
Maybe you could look in the manual of your monitor to change these settings to a larger number according to your desired screen resolution?

---

### Post by Vinze on 2006-09-14
Unfortunately I don't have a manual for my monitor. Please note that when using plain Xfce I do get the correct resolution. Also, I intentionally disabled compositing as that's just Xfce's compositing which has a bug.

---

### Post by frequenicity on 2006-09-14
> **Vinze said:**
> Oh, btw, could the window borders be theming issues?

I had the same issue with Window borders using the CGWD Themer at first. Do you have this installed? If so, does it clear up if you select a regular theme?

If that is the case then choose a CGWD theme and try typing:

> nohup cgwd --replace Into the terminal. 

If that works, then you are going to have to put that into either your /usr/bin/thefuture or /usr/bin/compiz-start depending on which version you are using.

My /usr/bin/thefuture: (no longer valid in newer version I believe)
> #!/bin/bash
gnome-window-decorator &  compiz --replace decoration wobbly water fade minimize cube rotate zoom scale move resize place switcher & **nohup cgwd --replace &**
xmodmap /usr/share/xmodmap/xmodmap.us

My /usr/bin/compiz-start:
> #!/bin/sh
if ps -e | grep Xgl > /dev/null
then
    nohup compiz --replace dbus csm > /dev/null &
else
    nohup compiz --strict-binding --indirect-rendering --replace dbus csm > /dev/null &
fi

sleep 2

if [ -f /usr/bin/cgwd ]
then
    **nohup cgwd --replace &**
else
    nohup gnome-window-decorator --replace &
fi

---

