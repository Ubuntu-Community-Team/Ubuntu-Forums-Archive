---
title: "Window borders, cube works fine (compiz)"
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by Bundai on 2007-04-21
Okay, sorry for making another thread about this but I thought I should.
The thing is, that I got the cube and wobbly thing working in compiz without beryl installed and its fine for me this way (I mean the integrated desktop effects thing in feisty). BUT I still mis the window borders (maximize, minimize, exit). And I have checked that there is that line in my xorg.conf file which everyone keeps talking about. Any suggestions?

And my xorg.conf screen section looks like this: 

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "SyncMaster"
    DefaultDepth    24
    Option "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Edit: And yeah I have geforce 7950gt

Edit2: And actually I can click the buttons but its completely transparent (window border).

---

### Post by Bundai on 2007-04-21
Oh my god. I got it to work, sorry I was a bit rushy by posting this post. I just did that ctrl + alt + backspace.

---

