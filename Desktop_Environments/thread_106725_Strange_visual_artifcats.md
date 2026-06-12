---
title: "Strange visual artifcats"
date: 2005-12-21
forum: Desktop Environments
---

### Post by bean1975 on 2005-12-21
I am getting [little black squares on minimize/maximize ]("http://www.ubuntuforums.org/showpost.php?p=553780&postcount=2") and ['slow' borders]("http://www.ubuntuforums.org/showthread.php?t=36062") . Both state that these are metacity problems. But I am seeing this in KDE, various versions (Hoary, Breezy, 3.5...), running binary nVidia drivers.

---

### Post by localzuk on 2005-12-21
Hi, could you post your xorg.conf file here? (it is in /etc/X11/xorg.conf).

---

### Post by bean1975 on 2005-12-22
Ommitted input and font settings. RenderAccel is commented out because when I switched it on, X froze solid for the first in the more than 1 yrs I have KDE on the machine.

> 
Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
        Option "RandRRotation" "on"
#       Option "RenderAccel" "true"
EndSection

Section "Monitor"
        Identifier      "DELL 2005FPW"
        Option          "DPMS"
        Modeline "1680x1050"  147.14  1680 1784 1968 2256  1050 1051 1054 1087
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18 [GeForce4 MX - nForce GPU]"
        Monitor         "DELL 2005FPW"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1680x1050"
        EndSubSection
EndSection

Section "DRI"
        Mode    0666
EndSection


---

### Post by bean1975 on 2006-01-17
Still no advancement in this.... help please.

---

### Post by Rumpty on 2006-01-17
Do you mean nested black rectangular outlines which redraw rapidly as you open/minimise a program? I see this if I have a few progs open at once, and open/minimise one of them. 

For instance, with a terminal open, gedit open, and nautilus open/minimise the black outlines appear. I realise this is on Ubuntu, not Kubuntu, but it does also occur on my Kubuntu (clean) installation, but more things have to be open there. 

I assumed this effect is related to the "slowness of the desktop" that people have complained about on the forums from time to time, and also relates to "which is faster, Ubuntu or Kubuntu?"

---

### Post by bean1975 on 2006-01-24
After lots of Googling the answer is crystal clear. I need RenderAccel on but for that I need nvidia-glx 1.0-8xxx. After talking with folks on IRC, it seems that once the driver stabilizes in Dapper, it'll be backported to Breezy. Either that or we wait 'till April for our RenderAccel.

---

