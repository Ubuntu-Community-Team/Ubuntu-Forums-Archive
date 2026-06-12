---
title: "Changing screen size in Ubuntu?"
date: 2007-03-12
forum: Desktop Environments
---

### Post by tonycm1 on 2007-03-12
Hey everyone, i'm really new to Ubuntu and wanted to know if it supports more than just the standard 1024x768 resolution at 60Hz?

I haven't installed a video card driver for my laptop yet and wanted to know if that may potentially be the reason for not getting any alternative settings?

The reason it bothers me so much is because I have a wide-screen laptop and 1024x768 just looks really odd compared to what I was used to before.

Thanks :)

---

### Post by chewearn on 2007-03-13
I suggest you go ahead an get the specific video driver first.  Is your video nvidia, ATI, or other?

In my case, I have one machine where the correct resolution is detected of the bat; on another, I have to manually configure it.

if installing the video driver doesn't do the trick, you need to edit xorg.conf.  Open a terminal, copy/paste these lines:

This will make a backup of the file.  In case you mess up, you can restore it:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
This will open the text editor, gedit:
```
sudo gedit /etc/X11/xorg.conf
```
Near the bottom of the file, you should see some lines like this:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
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
```Add the resolution you wanted, like this:
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```
Note in the example, I have added "1680x1050"; use the resolution you wanted.

Finally, to apply the changes:
```
sudo /etc/init.d/gdm restart
```

---

