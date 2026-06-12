---
title: "gdm runs but no desktop (After NVIDIA 180.22 install)"
date: 2009-01-11
forum: Desktop Environments
---

### Post by whisp3r3d-soul on 2009-01-11
Ok the problem is just as the title states I found this post from November [http://ubuntuforums.org/archive/index.php/t-968391.html](http://ubuntuforums.org/archive/index.php/t-968391.html) but I don't know how to do what wizardStan did

"wizardStan
November 2nd, 2008, 08:32 PM
SUCCESS!
Having identified the problem as being due to two video cards, I did a little bit more research, and solved the problem by adding a "BusID" line to my xorg.conf file.
ie:
Section "Device"
Identifier "Configured Video Device"
Driver "nvidia"
Option "NoLogo"
# Insert BusId here!
BusId "1:0:0"
EndSection

So, I'm guessing the version of X shipping with 8.04 and earlier did something intelligent when encountering two cards: checking for connections, or simply picking the first one, or something.
Presumably the version of X shipping with 8.10 does not do this. It sees two possible primary candidates, and gives up. Telling it which one to use via BusId seems to be the only sensible work around."

How to I do this from the terminal and how do I check my bus id's from the terminal? Hence why this is in the beginers corner. Thanks a ton

---

### Post by ushimitsudoki on 2009-01-11
Hey,

I can tell you that I have 180.22 running with two cards.

lspci will show your PCI busses

---

### Post by whisp3r3d-soul on 2009-01-11
OK I will look into that although I'm not sure about how to use that command IM sure I can find out the real question is though which file do I edit and how do I do it through the terminal?

 Also I failed to mention that I am using the not so common 7800 GT in sli mode this model as I found out has been known to have issues with ubuntu.

---

### Post by ushimitsudoki on 2009-01-11
I do a:
> jason@apollo:~/Desktop$ lspci
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GTS 512 (rev a2)
02:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GTS 512 (rev a2)

And, so in my /etc/X11/xorg.conf I have:
> Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS 512"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS 512"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Device"
    Identifier     "Videocard2"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS 512"
    BusID          "PCI:2:0:0"
EndSection

Note the first card is listed twice - to be honest, I don't know exactly why I think it is so it can run multiple monitors against the one card, but I'm not sure about that.

My cards are NOT in SLI - so I don't know if that changes anything.

/etc/X11/xorg.conf is the file to edit. It has to be done as root.

The nvidia driver install can also try to automatically set up your xorg.conf, if you want to give that a try. You will lose some customization to your X server if you go that route, but that may not matter if you haven't done any thing, and you can always back it up first.

---

### Post by whisp3r3d-soul on 2009-01-11
Awesome your suggestion is perfect except I ran into a weird error it is

(geedit:5809):Gtk-WARNING **: cannot open display:

I will keep working I can use a live disk to do this as well now that you have showed me how Ill be back if it doesn't work. "crossed fingers"

---

### Post by whisp3r3d-soul on 2009-01-11
ARRRGGG after spending all night surfing the net and the forums I am so close here is the final key to the puzzle which I cant find a straight answer for. 

How do I gain "meaning what are the steps" to gaining root privileges from a live CD so that I can edit my xorg.conf file.

The reason this is needed is the weird error it is throwing when I try to do it from the terminal. 

Thanks for all the help.

---

### Post by Mazin on 2009-01-11
```
sudo -s
```
will let you be root.

prefixing a command with "sudo":
```
sudo gedit /media/[your ubuntu partition]/etc/X11/xorg.conf
```
will run that command as root.

---

### Post by whisp3r3d-soul on 2009-01-12
Alright guys its been along haul with an extra reinstall thrown in cause everything got messed up.

In the end this is what worked out.

Reinstalled Ubuntu 8.1

installed recommended packages

Instead of installing NVDIA drivers 180.22 I installed recommended 177

Still had the same problem which I knew it would

reconfigured the xorg.config from LiveCD 

Worked with some bugs cleaned up the bugs and Presto all done!

Thanks for all your Help I call this CLOSED!:guitar:

---

