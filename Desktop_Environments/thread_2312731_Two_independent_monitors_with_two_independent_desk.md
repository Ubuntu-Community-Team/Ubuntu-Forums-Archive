---
title: "Two independent monitors with two independent desktops"
date: 2016-02-06
forum: Desktop Environments
---

### Post by cjsmall on 2016-02-06
OS: Xubuntu 15.10
GPU: Nvidia Quadro K4000 with nvidia-352-63 driver

I asked this question on the Xfce forum and got no responses, so I decided to repost the question here.

I have two independent monitors configured in a left-right setup using  the Nvidia X Server Settings tool.  The **/etc/X11/xorg.conf** file looks  like this:

```
Section "ServerLayout"     Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" LeftOf "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Planar Systems, Inc."
    ModelName      "PX212M"
    HorizSync       31.0 - 92.0
    VertRefresh     56.0 - 86.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Planar Systems, Inc."
    ModelName      "PX212M"
    HorizSync       31.0 - 92.0
    VertRefresh     56.0 - 86.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro K4000"
    BusID          "PCI:4:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro K4000"
    BusID          "PCI:4:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "DVI-I-0: nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DP-2: nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

When I login I get my standard xfce4 desktop on the right screen (**DISPLAY :0.0**) which has the xfce4-panel.

To  the left (**DISPLAY :0.1**), I get an empty default xfce4 background  image.  However, this is being managed by the same desktop manager as  the right screen.  There is no panel on the left screen, and if I type **xfce4-panel --display :0.1** on either screen I get the message: "*xfce4-panel: There is already a running instance*"

Here are the relevant xfce4 and window management process that are actually running:


```
/usr/sbin/lightdm
/usr/bin/X -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp vt7 -novtswitch lightdm --session-child 12 19
/bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
xfce4-session
/usr/lib/x86_64-linux-gnu/xfce4/xfconf/xfconfd
xfce4-panel --display :0.0 --sm-client-id [UUID]
xfsettingsd --display :0.0 --sm-client-id [UUID]
xfdesktop --display :0.0 --sm-client-id [UUID]
```

I can right-click on the left screen and get the desktop menu which  allows me to open certain applications on that screen.  For example, I  can set a separate wallpaper on display **:0.1** and open applications like a web browser.  However, when I try to  open an **xfce4-terminal**, one appears while some of the  **xfce4-terminals** already opened on display **:0.0** are blown away -- and vice versa.   (This is likely some strange coding bug in xfce4-terminal.)

I'm not sure why **xfdesktop --display :0.0** is managing display **:0.1** as **Xinerama** is not enables.

What  I want is to have two completely independent desktop/window managers  with independent xfce4-panels, running on each monitor, with only the  mouse being able to move between the two screens.  The **startx** command has a display option (not well documented) but most of the other desktop commands do not.

There  are a number of posts from 2011-2012 asking about this, but no clear  solutions.  I've been running in this two-headed mode on a Sun Solaris  system with the openwin (i.e. gnome) desktop for the past 20 years or  so.  Yet, I have not been able to find any documentation on how to  configure this for Xubuntu.  Does anyone have the solution?  Any  pointers would be greatly appreciated.

---

### Post by echo59 on 2016-03-29
Hi,

I seem to be having a similar problem to you.  I've no experience at all managing 2 screens.  Any advice you can give me?  My thread is at [http://ubuntuforums.org/showthread.php?t=2318669](http://ubuntuforums.org/showthread.php?t=2318669)

Any advice or suggestions you can give me would be much appreciated.

---

