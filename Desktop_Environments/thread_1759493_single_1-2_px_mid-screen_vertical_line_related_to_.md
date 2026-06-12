---
title: "single 1-2 px mid-screen vertical line related to resolution"
date: 2011-05-15
forum: Desktop Environments
---

### Post by David Haas on 2011-05-15
On my Asus laptop, Ubuntu 11.04 or 9.04 defaults to a monitor resolution of 1680x1050, and looks good. But when any lower resolution is chosen, such as 1440x900, a central black vertical line from the top to the bottom of the screen appears. It's thin - about 1-2 px wide. No such line appears with Ubuntu 8.04 at its default resolution of 1680x1050 or lower. I tried to eliminate the line by adding an xorg.conf file. I did write a file that works well, but it gives the same line with all resolutions below 1680x1050.

Here is my xorg.conf file:
Section "Device"
        Identifier      "ATI Technologies Inc M26 [Radeon Mobility X700]"
        Driver          "ati"
EndSection         

Section "Monitor"
        Identifier      "Laptop Monitor"
        HorizSync       48.0 - 54.0
        VertRefresh     59.0 - 60.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Laptop Monitor"
        Device          "ATI Technologies Inc M26 [Radeon Mobility X700]"
        DefaultDepth    16
        SubSection "Display"            
                Depth    16
                Modes    "1680x1050" "1440x900" "1280x800"
        EndSubSection
EndSection 

Then I tried PCLinuxOS 12.10 and openSUSE 11.04 and saw that they gave the same result as Ubuntu 11.04: defaults of 1680x1050 without the line, but presence of the line with lower resolutions. Their dialog boxes for changing monitor resolution did, however, look to be identical to Ubuntu's.  

So, has anyone seen this glitch or have some ideas as to its cause?

---

