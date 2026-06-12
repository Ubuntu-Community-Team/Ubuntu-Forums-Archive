---
title: "Desktop Effects"
date: 2007-10-04
forum: Desktop Effects &amp; Customization
---

### Post by silv3rback on 2007-10-04
Hi Guys,

Im new to the forums and to Linux. I installed Ubuntu 7.0.4 about a week back and then a friend of mine advised the Ultimate. The downloads for the DVD are crawling along so I downloaded the CD iso... Anyway,

When I had Ubuntu 7.0.4 installed I could apply the desktop effects, with the "Windows wobble when Moved" and "Workspace on a Cube" perfectly, but when I installed Ultimate 1.4 I couldnt do this:(
I can tick the two blocks, but my theme seems to cut off the top bar (with File, Edit and the minimize, maximize and ext options) meaning I cant move any of the windows

Im loving Linux btw, went from using Windows for my entire life, straight into Linux, no more Windows for me:)

---

### Post by KitChy on 2007-10-04
A few questions. What GFX card are you using? And do the rest of the "effects" work? e.g. 3D cube etc....

---

### Post by silv3rback on 2007-10-04
> **KitChy said:**
> A few questions. What GFX card are you using? And do the rest of the "effects" work? e.g. 3D cube etc....

nVidia 7600GS. I didnt have the problem before, I could run all of the effects, now I cant run any:(

---

### Post by KitChy on 2007-10-04
Edit your "xorg.conf" file and add the following to your "Screen Section"

```
Option 	   "AddARGBGLXVisuals" "True"
```

And then you need to restart X [ctrl+alt+backspace]

---

### Post by silv3rback on 2007-10-04
OK, I've had a look at the xorg.conf file and Im a touch confused. Sorry dude, Im a complete Linux no0b, still getting started with it. I have two Screen Sections, can you tell me where it should go

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

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900 +0+0; 800x600 +0+0; 640x480 +0+0"
EndSection
```

---

### Post by KitChy on 2007-10-04
I believe it's the 2nd part from your xorg.conf file! If that fails, just remove it and add it to the other part, but i'm pretty sure it goes under the 2nd section!

---

