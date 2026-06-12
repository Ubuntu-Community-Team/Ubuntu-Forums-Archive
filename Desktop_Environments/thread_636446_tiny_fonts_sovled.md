---
title: "tiny fonts sovled?"
date: 2007-12-09
forum: Desktop Environments
---

### Post by GreyShadow on 2007-12-09
In a recent update on my daughter's computer all the fonts were changed to  a very tiny size esp.
in Firefox. Most of the "problem" was fixed by changing the resolution in
Appearance-Fonts-Details-Resolution from 50 to 60 dots per inch. Quick fix
for an annoying problem!:confused:

---

### Post by UBCToad on 2007-12-23
There are many web pages that give the following instructions on resolving small font issues on Ubuntu:
Edit your /etc/X11/xorg.conf file and add the following lines to the Monitor section:
#   DisplaySize     270    203   # 1024x768  96dpi
#   DisplaySize     338    203   # 1280x768  96dpi
#   DisplaySize     338    254   # 1280x960  96dpi
#   DisplaySize     338    270   # 1280x1024 96dpi
#   DisplaySize     345    195   # 1360x768  96dpi
#   DisplaySize     370    277   # 1400x1050 96dpi
#   DisplaySize     423    370   # 1600x1400 96dpi
#   DisplaySize     423    318   # 1600x1200 96dpi

Uncomment the line that applies to your screen resolution (Remove the first # character from the start of the line).
If your resolution is not listed here you can add it.  The two numbers are based on your resolution.  The first number is related to your screen's width and the second is related to your screen's height (widthxheight 96 dpi in the examples above).  The first number is width / desired DPI * 25.4.  The second number is height / desired DPI * 25.4.

Once this is done reboot your X server (NVidia users see below first).  This can be done by either rebooting your computer OR logging out of all appications and pressing Ctrl - Alt - Del.

NVidia drivers seem to ignore the lines described above.  They use your monitor's EDID setting (which may not be what you want).  To override their settings edit your /etc/X11/xorg.conf and add the following line to your Device or Screen section:
    Option         "DPI" "100 x 100"
You can try other numbers for the DPI but this is what I used.  Then restart your X server as described above.
This information was found on the following web page:
[http://us.download.nvidia.com/XFree86/Linux-x86/169.04/README/appendix-b.html](http://us.download.nvidia.com/XFree86/Linux-x86/169.04/README/appendix-b.html)

This solved my Small Font Resolution Size Problem on Ubuntu 7.10 using an NVidia 8800GT connected to a high definition TV.

---

### Post by ODF on 2007-12-30
Adding this to my Device section fixed the problem in my case.

```
Option "DPI" "100 x 100"
```

I'm using a 720p tv wich seemed to be the cause.

I forgot to mention my vidéo card : GeForce 8800 GTS

Thank you UBCToad !

---

