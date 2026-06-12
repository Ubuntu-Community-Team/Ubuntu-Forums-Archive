---
title: "visual effects don't work"
date: 2007-11-18
forum: Desktop Effects &amp; Customization
---

### Post by fiveape on 2007-11-18
[SIZE="2"]Hello everyone:)...! I'm kind of new in LinuX so I want some kind of help.
I bought a laptop HP Pavilion dv2000, and I run Ubuntu 7.10.
But, the system doesn't recognize  my graphic card, which is Intel graphics media accelerator X3100 with 251 ram , as a  result  I can't enable visual effects:confused:
Also I didn't find any drivers....:(

Any help please...?:)[/SIZE]

---

### Post by daengbo on 2007-11-18
It looks like you need to use the intel driver. Looking at System -> Administration -> Screens and Graphics, what driver are you using? According to [this page]("http://www.intellinuxgraphics.org/documentation.html"), you can choose the X3100 by defining your card as a 965.

Good luck

---

### Post by fiveape on 2007-11-18
I was using 740 (generic) , 
I tested 965 driver, but didn't work ....:confused:

---

### Post by fiveape on 2007-11-20
Any advice please?:confused:

My problem is yet not solved, and also I don't know what to do...
to fix desktop effects...:confused:
Thanks:)

---

### Post by Forlong on 2007-11-22
What's the output of ```
compiz
``` in a terminal?

---

### Post by fiveape on 2007-11-22
When I typed 'compiz' this is what it displayed...
> vitor@vitor-laptop:~$ compiz

Cheking for Xgl: not present.

No whitelisted driver found

aborting and using fallback: /usr/bin/metacity

then it "froze" 
until I typed two times 'exit'...

Any advice...:)?

---

### Post by Ub1476 on 2007-11-22
Your graphic card has been blacklisted! Read more about it [Link (sticky on top)]("http://ubuntuforums.org/showthread.php?t=582112"). 

Hope that helps:)

---

### Post by fiveape on 2007-11-22
Yes , indeed my graphic card is blacklisted :(....
I typed the following :```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

but , unfortunately   nothing changed:confused:... 

am i  something missing....?:?

---

### Post by Ub1476 on 2007-11-22
If you copied/pasted exactly the same as on the sticky, it should probably work. You tried to enable visual effects again, right?

---

### Post by ryphix on 2007-11-22
[http://ubuntuforums.org/showpost.php?p=3654273&postcount=20](http://ubuntuforums.org/showpost.php?p=3654273&postcount=20)

---

### Post by fiveape on 2007-11-22
Yes , that's right.:confused:
I copy/paste it exactly as the one on the sticky.

Also, I modified the source code of compiz as ryphix told me , 
but even then it  didn't work.:(

Is anything else I could try...? or 
Should I reinstall Ubuntu , and then try again your advices...?

---

### Post by Forlong on 2007-11-23
Post the output of ```
compiz
``` in a terminal again.

---

### Post by fiveape on 2007-11-24
The output of the```
compiz
```
is the following ```
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: not present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Starting gtk-window-decorator
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by mrmiserable on 2007-11-24
can you post your xorg.conf

---

### Post by fiveape on 2007-11-24
Could you explain me how I would see my "xorg.conf":confused:?

---

### Post by Forlong on 2007-11-24
You can use this command to post it:
```
grep -v ^# /etc/X11/xorg.conf
```

But generally, just open /etc/X11/xorg.conf in your favorite text editor.

---

### Post by mrmiserable on 2007-11-24
/etc/X11/xorg.conf

this is the route to the file then copy paste

sorry thanks forlong

---

### Post by fiveape on 2007-11-24
Thank you:),
Typing this command ```
grep -v ^# /etc/X11/xorg.conf
```
It displayed:```
Section "Files"
EndSection

Section "Module"
        Load            "glx"
        Load            "GLcore"
        Load            "dri"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection


Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "Intel 965"
        Busid           "PCI:0:2:0"
        Driver          "i810"
        Screen  0
        Vendorname      "Intel"
EndSection

Section "Monitor"
        Identifier      "Failsafe Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 640     480
                Modes           "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "device" # 
        Identifier      "device1"
        Boardname       "Intel 965"
        Busid           "PCI:0:2:0"
        Driver          "i810"
        Screen  1
        Vendorname      "Intel"
EndSection
Section "screen" # 
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
        SubSection "Display"
                Depth   24
                Modes           "640x480@60"
        EndSubSection
EndSection
Section "monitor" # 
        Identifier      "monitor1"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection
Section "device" # 
        Identifier      "device2"
        Boardname       "Intel 965"
        Busid           "PCI:0:2:1"
        Driver          "i810"
        Screen  0
        Vendorname      "Intel"
EndSection
Section "screen" # 
        Identifier      "screen2"
        Device          "device2"
        Defaultdepth    24
        Monitor         "monitor2"
        SubSection "Display"
                Depth   24
                Modes           "640x480@60"
        EndSubSection
EndSection
Section "monitor" # 
        Identifier      "monitor2"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection

```
Any suggestion...?:)

---

### Post by fiveape on 2007-11-25
Can anyone help me...?
It still can't work...:(

Thank you:).

---

### Post by Forlong on 2007-11-25
Since it says something about a failsafe device, reconfiguring the xorg.conf is always worth a try:;
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by fiveape on 2007-11-26
Thank you Guys :),
Finally the visual effects worked\\:D/...
This is what i did.
I reinstalled Ubuntu , and then I typed _[COLOR="Red"]once[/COLOR]_ the following code ```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

Thanks to you ,it really worked,
I'm grateful for your help....:)

---

