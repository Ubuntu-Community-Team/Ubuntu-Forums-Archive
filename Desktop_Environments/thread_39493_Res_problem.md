---
title: "Res problem"
date: 2005-06-05
forum: Desktop Environments
---

### Post by SparkyDawg on 2005-06-05
I booted up into Ubuntu to have everything 640x480. When I go into screen resolution, the res is unchangable. I have no clue how to fix this and was wondering if this has ever happened to any of you before. I've tried rebooting, but that didnt work either. Help?

---

### Post by netrattler on 2005-06-05
You are going to need to edit your /etc/X11/xorg.conf file, mine did the same thing and would only give me a max of 1024x768 even though my monitor would do much higher. One thing you want to check if you have a CRT monitor is the "Section Monitor" and see if it has your correct HorizSync and VertRefresh, you can find the specs from the manufacturer website. Hoary didn't pick it correctly for me. You will also need to edit the "Section Screen" as well and just add the resolutions that your monitor support. For example I wanted to run my monitor at 1280x1024 but was only given me 1024x768, so what I did was add "1280x1024" in front of "1024x768". Here is an example of my screen section so you can get an idea. Also once you saved you xorg.conf file to make the changes take effect you will need to logout and press CTRL-ALT-Backspace key to reload your xorg.conf file.

Hope this helps you out,
Joe

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480" "1x1"
        EndSubSection
EndSection

---

