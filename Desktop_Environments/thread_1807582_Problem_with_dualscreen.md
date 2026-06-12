---
title: "Problem with dualscreen"
date: 2011-07-19
forum: Desktop Environments
---

### Post by bakie on 2011-07-19
Hello,

I have a problem with dual screening. Actually with triple screening. I have 2 graphics card and use them to connect 3 screens. The two screens connected to one graphics card are in use as one big desktop with a resolution of 2560 x 1024. The other screen connected to the other graphics card is using a resolution of 1920 x 1080. Now my problem is with the big desktop, when maximizing a window it uses a maximum width of 1920 and a height of 1024. This is very annoying. Now my question is, is there a way to limit the width size to 1280 so it will remain on one screen ?
As you can see in the image, the window should only come to the second feet located above :).

Thx in advance

---

### Post by Brad55 on 2011-07-19
bakie here are a couple sceenshot of my desktop. I'm using an Nvidia card and 2 1680x1050 monitors with TwinView set in the Nvidia settings.

This one is Ubuntu 10.04 with Nvidia and it's in TwinView.
[[IMG]http://img851.imageshack.us/img851/2945/screenshot9k.th.jpg[/IMG]](http://imageshack.us/photo/my-images/851/screenshot9k.jpg/)

This one is when I had SUSE on the computer. I had the same setup.
[[IMG]http://thumbnails31.imagebam.com/8835/67471288347838.jpg[/IMG]](http://www.imagebam.com/image/67471288347838) 
I don't know why this was happening in KDE on openSUSE but it was.

Are you using an Nvidia card?
Which screen do you have set as #0 default screen?

These sites might help you out.
[How-to-set-up-multiple-monitors-in-linux]("http://www.instructables.com/id/How-to-set-up-multiple-monitors-in-linux/")
[hdual-monitors-with-nvidia]("http://www.ubuntugeek.com/dual-monitors-with-nvidia.html")
[LinuxAndDualMonitors]("http://www.yolinux.com/TUTORIALS/LinuxAndDualMonitors.html")

---

### Post by bakie on 2011-07-19
I forgot to mention what card it is, I am using 2 ATI Radeon HD 3780. I can't use Xinerama because then compiz doesn't work anymore. And my default screen is the most left one. The setup is 0 1 2 where 0 and 1 are two 19" screens making use of one big desktop and then 2 is my 23" screen.
So the problem is the 23"screen, it uses a different resolution and that's why programs in full screen use two-third of the big desktop (screen 0 and 1).

---

### Post by Brad55 on 2011-07-20
bakie here is my x11conf. I dont know if this will help, but may be you can look at it and find what you need to change in yours.

```
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

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 260"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 260"
    BusID          "PCI:2:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "TwinView" "0"
# Removed Option "metamodes" "DFP-1: nvidia-auto-select +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-0: nvidia-auto-select +1680+0, DFP-1: nvidia-auto-select +0+0"
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
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by bakie on 2011-07-20
I figured out the problem, apparently the problem was with compiz itself. In CompizConfig Settings Manager ther is general options and in there, there is a tab display settings. There you got Overlapping Output Handling, I changed it to Prefer smaller output and now the screen remains on one screen instead of overlapping :). Figured out the problem was with compiz when I did a fresh install because of some problem in my / partition.

Thx for the help tho Brad55 :)

---

