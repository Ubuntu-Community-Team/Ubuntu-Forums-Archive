---
title: "HELP!!!!! no top after using Compiz Fusion..."
date: 2007-09-16
forum: Desktop Effects &amp; Customization
---

### Post by WACD on 2007-09-16
i installed compiz fusion through a few ways...
but they all had the same common problem...
n that is after i install compiz fusion...
after i run it...
the top of my windows are gone...
n I can't move or close the windows...
i read some posts about going to windows decoration...
but then i tried that n it didn't work...
so i was just wondering is it hardware problem...
or is there anything that i don't know...

i'm using the bullet proof installation that i found in this forum...
everything works else then the top...

and a little about my graphics info...
i'm using a Nvidia 7600GT...
dual monitor...
both LG...
one is a 22" wide...running on 1680x1050...
the other one is a 19" square...running on 1280x1024...

hope i can get my problem solved thank you...

---

### Post by praet on 2007-09-17
Try running compiz like this:

```
compiz --replace && gtk-window-decorator --replace
```

Or you can use emerald as the window decorator, as well as kde-window-decorator if you are using kubuntu.

---

### Post by WACD on 2007-09-17
well i'm using ubuntu...
but then i did what u said before...
yet it still doesn't work...
i am using that bullet proof version of the compiz fusion...
n there is a setting is call...
select windows manager...
there is three options...
which is compiz...
metcity and kWin...
well...
if i select compiz...
i get all the effects...
but then there won't be top...
if i select either one of the other two...
i will get tops...but no effects at all...

---

### Post by Forlong on 2007-09-17
Have a look at what I wrote [here]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion") in the *Troubleshooting* section under "No window boarders (titlebars)".

---

### Post by WACD on 2007-09-17
thank you...
well...
I did everything on those pages that I found through your links...
I even reinstalled compiz fusion the same way...
but then...
the same thing still happens...
the top is missing...
n after i run compiz fusion...
i can't even do [alt]+[F2]...

---

### Post by Forlong on 2007-09-18
> **WACD said:**
> the top is missing...
n after i run compiz fusion...
i can't even do [alt]+[F2]...
This means Compiz ain't running at all.
Please post the output of
```
compiz --replace
```
in the terminal.

---

### Post by WACD on 2007-09-18
well supposely it is running...
becuz i can haf all the other effects that compiz fusion gives me...
well if i type compiz --replace in terminal...
i don't get any reading...
the only thing happens is that it turns on compiz n i lose all my tops...

---

### Post by praet on 2007-09-19
WACD,
try running this command in a terminal:
```
compiz --replace && gtk-window-decorator --replace
```

Are you using KDE? if so, you will need to install compiz-kde.

---

### Post by Metallion on 2007-09-19
Try this one
```

compiz --replace --indirect-rendering

```

This one fixed the same problem for me before.

---

### Post by AriciU on 2007-09-19
You either mixed repos or have an older version of emerald installed.

sudo apt-get remove emerald emerald-themes && sudo apt-get install emerald emerald-themes

compiz --replace && emerald --replace &

---

### Post by UbuntuniX on 2007-09-19
I have the same card, I found a fix on Beryl forums (yes it also fixes Compiz).

```
gksudo gedit /etc/X11/xorg.conf
```

Add this line to the Screen section:
```
        Option          "AddARGBGLXVisuals"     "true"
```

You'll also need to add it to the graphics device section, it will say something like this: > "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GT]"

Emerald doesn't work for me. After one update it worked, then after the next it stopped working again.

Good luck. ;)

---

### Post by WACD on 2007-09-19
when I type compiz --replace && gtk-window-decorator --replace

this is the output that I got...

(gtk-window-decorator:7515): Wnck-WARNING **: Unhandled action type (nil)

---

### Post by WACD on 2007-09-19
if i type in compiz --replace and then run it first...
n then open a new terminal n then type in emerald --replace...
i get this out put from emerald...

Segmentation fault (core dumped)

what does that mean...?

---

### Post by HokeyFry on 2007-09-19
i just had this issue like 5 mins ago, heres what i did

1. go to the autostarted applications program. i dont know what its called for you, i use xubuntu, but chances are its the same thing.

2. add a new menu item. the name and description dont matter, but the command should be ```
compiz --replace
```

3. do the same thing as 2, but this time name the command ```
emerald --replace
```

4. press ctrl+alt+backspace (or log out) and log back in


if tis doesnt solve it, sorry man, this is what fixed it for me


EDIT: sorry, you posted the last message while i was typing this, im not sure if this will help you

---

### Post by WACD on 2007-09-19
this is my /etc/X11/xorg.conf reading...

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Thu Nov  9 17:55:59 PST 2006

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Thu Nov  9 17:56:28 PST 2006

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "LG L226W"
    HorizSync       28.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "DFP-0: 1680x1050_60 +0+0, DFP-1: 1280x1024_60 +1680+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

i haf dual monitor...
but here I only got one down...
will that be a problem...?

UbuntuniX:
I already had Option "AddARGBGLXVisuals” “True" in the script before you told me to add it...
but then I added the device part...
I don't kno do I got it right...

---

### Post by praet on 2007-09-20
Heres what mine Device section looks like:
```

Section "Device"
	Identifier	"nVidia Corporation G70 [GeForce 7600 GS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	#added below for lcd monitor
	Option		"UseDisplayDevice"	"DFP"
EndSection
```


"Segmentation fault (core dumped)"  Means that emerald has crashed.

---

### Post by zir0n on 2007-09-21
Hi all, i fixed the missing border problem by adding this to device section of my xorg config file located at /etc/X11/

```
Section "Device"
    Identifier     "nVidia Corporation GeForce Go 7900 GS"
    Driver         "nvidia"
    Option         "AddARGBVisuals"     "True"
    Option         "AddARGBGLXVisuals"  "True"
EndSection

```

then running "compiz --replace" and gtk-window-decorator"
and reboot if it doesn't work immediately

Edit:
I forgot to mention I installed the latest Nvidia drivers using Envy

---

