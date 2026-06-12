---
title: "Im really trying but cant get compiz to work please help me"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by playme123 on 2007-11-08
I have compiz installed but cant get it to work, managed to get near enough yesterday was able to make the cube but not to resize it.  I then rebooted and me cube had gone.
Im using gutsy and have a radeon 9200se graphics card.

Please help me Iv tried for over a day and still cant do it.


Also please me gentle iv only just come back to playing with ubuntu:(

---

### Post by TadH on 2007-11-08
what exactly is the problem? "i cant get it to work" is pretty broad haha

---

### Post by playme123 on 2007-11-08
basically I cant get my cube back and if and when I get it back I cant seem to resize it

---

### Post by ukripper on 2007-11-08
take screenshot of your screen while you resize and post it here

---

### Post by Rafadagaffer on 2007-11-08
I used this guide to get Compiz to work on Feisty. [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385). That is for Feisty though so I dont know if that will work. 

I got Compiz to start by adding it to the list of startup programs System>>>Adminstration>>>Sessions>>>New. The name for new session was Compiz and the command was compiz --replace. Its all there in that tutorial but like I said that is for Feisty so I dont know how well it will work

---

### Post by playme123 on 2007-11-08
> **ukripper said:**
> take screenshot of your screen while you resize and post it here

I would do a screenshot but cant even get the cube back:(

---

### Post by playme123 on 2007-11-08
anyone

---

### Post by playme123 on 2007-11-08
pleasssssssssssssssssssssseeeeeeeeeeeeeeeeeeeeeeeeeeee

---

### Post by Forlong on 2007-11-08
So Compiz runs OK?
[Here's](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion) how you can get the cube working (under "Getting the cube"). Hope it helps.

---

### Post by playme123 on 2007-11-09
I followed your guide last time and it worked then I couldnt resize the cube, how can I uninstall compiz and all the other components and re install.  Its not even letting me tick the cubes in the compizconfig settings

---

### Post by playme123 on 2007-11-09
when I type compiz in the terminal this is the output

onna1@donna1-desktop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0

---

### Post by Forlong on 2007-11-09
Are you still on Feisty? How did you install Compiz Fusion?

---

### Post by playme123 on 2007-11-09
nh im on gutsy installed it using the sync package manager, thanks for replying so quickly this is proper driving me nuts

---

### Post by Forlong on 2007-11-09
Please post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by playme123 on 2007-11-09
got the output weres this code tag thing

---

### Post by Forlong on 2007-11-09
In the panel above the message field that starts with[B]
B[/B]* I* _U_

---

### Post by playme123 on 2007-11-09
donna1@donna1-desktop:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-bcop                                0.5.2-0ubuntu1                       Compiz option code generator
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1           Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1           Compiz configuration settings manager
rc  emerald                                    0.3~git20070717-0ubuntu1             Decorator for compiz-fusion
ii  gnome-compiz-manager                       0.10.3-0ubuntu2                      Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1           Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1             Decoration engines for compiz-fusion
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu2                      Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings
donna1@donna1-desktop:~$ 

really sorry looked above b and and there was nothing there

---

### Post by gspat on 2007-11-09
I believe you are using the quick reply area... try using the "post reply" link instead.

---

### Post by playme123 on 2007-11-09
```
donna1@donna1-desktop:~$ dpkg -l | grep compiz
ii  compiz                                     1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-bcop                                0.5.2-0ubuntu1                       Compiz option code generator
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager
ii  compiz-fusion-plugins-extra                0.5.2+git20070928-0ubuntu1           Collection of extra plugins from OpenComposi
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2           Collection of plugins from OpenCompositing f
ii  compiz-gnome                               1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - GNOM
ii  compiz-plugins                             1:0.6.0+git20071008-0ubuntu1.1       OpenGL window and compositing manager - plug
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1           Compiz configuration settings manager
rc  emerald                                    0.3~git20070717-0ubuntu1             Decorator for compiz-fusion
ii  gnome-compiz-manager                       0.10.3-0ubuntu2                      Compiz Gnome Manager
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1           Settings library for plugins - OpenCompositi
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3           Settings library for plugins - OpenCompositi
ii  libemeraldengine0                          0.3~git20070717-0ubuntu1             Decoration engines for compiz-fusion
ii  libgnome-compiz-manager0                   0.10.3-0ubuntu2                      Compiz Gnome Manager
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1           Compiz configuration system bindings
donna1@donna1-desktop:~$ 


```

---

### Post by playme123 on 2007-11-09
> **gspat said:**
> I believe you are using the quick reply area... try using the "post reply" link instead.

I think ive done it thanks for that:)

---

### Post by Forlong on 2007-11-09
Alright and what gives ```
fglrxinfo
``` as well as ```
glxinfo | grep "direct rendering"
```

---

### Post by playme123 on 2007-11-09
```
donna1@donna1-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 8x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.1


```

---

### Post by playme123 on 2007-11-09
```
donna1@donna1-desktop:~$ glxinfo | grep "direct rendering"
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
donna1@donna1-desktop:~$ 

```

---

### Post by WakkiTabakki on 2007-11-09
Sound like you're using the wrong driver for your video card. Have you enabled the restricted driver (fglrx I think its called for the ATI-cards, I'm a Nvidia-guy myself, so...)?
Check 'System / Administration / Restricted Driver Manager'
If nothing in there tips you off, post whats in the "Device"-section of the file /etc/X11/xorg.conf

/Niklas

---

### Post by Forlong on 2007-11-09
OK... I thought you had the "restricted" driver installed, because you are running Xgl.

Do you want to use the proprietary driver from ATI? Then you have to install it via *System &#8594; Administration &#8594; Restricted Drivers Manager*

Please post your /etc/X11/xorg.conf as well. There might be some issues with a lowend ATI card like yours.

---

### Post by WakkiTabakki on 2007-11-09
Go follow this thread, Someone's having the same prob:
[http://ubuntuforums.org/showthread.php?t=607386](http://ubuntuforums.org/showthread.php?t=607386)

/N

---

### Post by playme123 on 2007-11-09
> **Forlong said:**
> OK... I thought you had the "restricted" driver installed, because you are running Xgl.

Do you want to use the proprietary driver from ATI? Then you have to install it via *System &#8594; Administration &#8594; Restricted Drivers Manager*

Please post your /etc/X11/xorg.conf as well. There might be some issues with a lowend ATI card like yours.

it says my hardware doesnt need the restricted drivers

---

### Post by playme123 on 2007-11-09
```
donna1@donna1-desktop:~$ /etc/X11/xorg.conf 
bash: /etc/X11/xorg.conf: Permission denied
donna1@donna1-desktop:~$ 


```

---

### Post by Forlong on 2007-11-09
> **playme123 said:**
> it says my hardware doesnt need the restricted drivers
Alright, then you can safely remove xserver-xgl again.

Use this command in a terminal for the xorg.conf:
```
grep -v ^# /etc/X11/xorg.conf
```

---

### Post by playme123 on 2007-11-09
```
donna1@donna1-desktop:~$ /etc/X11/xorg.conf 
bash: /etc/X11/xorg.conf: Permission denied
donna1@donna1-desktop:~$ grep -v ^# /etc/X11/xorg.conf

Section "Files"
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
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "X15-2"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV280 [Radeon 9200 SE]"
        Monitor         "X15-2"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

EndSection
donna1@donna1-desktop:~$ 


```

---

### Post by Forlong on 2007-11-09
After you removed Xgl, what's the output of ```
compiz
``` now?

---

### Post by WakkiTabakki on 2007-11-09
(First things first, the obligatory disclaimer) 
Again, I'm an Nvidia-bloke, the stuff here is compiled from this post and I have not tested it myself...
[http://ubuntuforums.org/showthread.php?t=550082&highlight=compiz+ati+9200&page=2](http://ubuntuforums.org/showthread.php?t=550082&highlight=compiz+ati+9200&page=2)


1. Make a backup of your current config
```
cp /etc/X11/xorg ~/Working-xorg-conf
```

2. Open your xorg.conf in the text edit app (need to open with admin rights using gksu)
```
gksu gedit /etc/X11/xorg.conf 
```

3. Find the "Device"-section and add the line
```
Option          "XAANoOffscreenPixmaps"
```

4. Find the "ServerLayout"-section and add
```
Option          "AIGLX" "true"
```

5. Add the following sections if they aren't already in there...
```

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

6. Save and restart the gui. Loggin out and then in again should do it...


Finally, if/when something cr*ps up...
If X refuses to start after this adventure simply do the following to restore your x-config:
1. Switch to VT1 (Press Ctrl-Alt-F1)
2. Restore the previous xconfig (the one you bakced up in step 1 above, 'cause, you did, right!?!)
```
sudo cp ~/Working-xorg-conf /etc/X11/xorg.conf
```
3. Restart X
```
sudo /etc/init.d/gdm restart
```

Good luck
/N

---

### Post by playme123 on 2007-11-09
```
donna1@donna1-desktop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with fglrx ATi drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :1.0



```

---

### Post by WakkiTabakki on 2007-11-09
Hmm ok... Also try adding 
```
        Option          "AccelMethod"    "XAA"
```
To your Device-section in /etc/X11/xorg.conf

And also change
```
Option          "XAANoOffscreenPixmaps"
```
to
```
Option          "XAANoOffscreenPixmaps"     "true"
```

Shouldn't make a differnce, but you never know...

Reboot the computer and see if that helps
/N

---

### Post by WakkiTabakki on 2007-11-09
Aaand, also uninstalling xserver-xgl may help. The open source ati driver supports aiglx so xgl isn't needed (and may interfere).

/N

---

### Post by playme123 on 2007-11-09
I went ahead and done the above, it all went tits up.  So done a fresh install and its working just need to figure out how to resize the cube.

---

### Post by WakkiTabakki on 2007-11-09
sweet...

What do you mean by "resize the cube"? 

/N

---

### Post by playme123 on 2007-11-09
make the pages smaller ie not full screen about 3 quarters of the size

---

### Post by WakkiTabakki on 2007-11-09
sorry, mate, I may be daft here, but...

You mean, when rotating the cube to access another desktop, you want the cube thing to zoom out?


/N

---

### Post by playme123 on 2007-11-09
> **WakkiTabakki said:**
> sorry, mate, I may be daft here, but...

You mean, when rotating the cube to access another desktop, you want the cube thing to zoom out?


/N

nah I just want all the pages to be a wee bit smaller, sorry if im driving you insane with my stupidity:lolflag:

---

### Post by WakkiTabakki on 2007-11-09
> **playme123 said:**
> nah I just want all the pages to be a wee bit smaller, sorry if im driving you insane with my stupidity:lolflag:

Yup, I can take about another 7 min before heading down the pub to salvage what's left of my self-esteem :)

What pages? wee bit smaller in what way... Any chance of you posting a screenshot, or something...

Cheers
/N

---

### Post by playme123 on 2007-11-09
pmsl dont blame you for want ing to head to the pub, I drive me self insane.  Right what im wanting is all the pages within the cube to be smaller.


Have a large whisky when you get to the pub you deserve one

---

### Post by WakkiTabakki on 2007-11-09
> **playme123 said:**
> pmsl dont blame you for want ing to head to the pub, I drive me self insane.  Right what im wanting is all the pages within the cube to be smaller.
Ahh, so you want the cube face larger than the image of the desktop showing on the face of the cube... sort-of, to get a frame-thing going around the image of the desktop?
Not sure of thats possible. Haven't seen it mentioned anywhere, though...

> **playme123 said:**
> Have a large whisky when you get to the pub you deserve one
Well, being in Sweden, that'd require another mortgage on the house...:sad:

I'm off!
/N

---

### Post by playme123 on 2007-11-09
> **WakkiTabakki said:**
> Ahh, so you want the cube face larger than the image of the desktop showing on the face of the cube... sort-of, to get a frame-thing going around the image of the desktop?
Not sure of thats possible. Haven't seen it mentioned anywhere, though...


Well, being in Sweden, that'd require another mortgage on the house...:sad:

I'm off!
/N

yeh thats it

you find an answer to this ill send you some over:lolflag:

---

### Post by Forlong on 2007-11-09
In ccsm go to Rotate Cube. There's an option for Zoom.
I guess that's what you're looking for.

---

### Post by playme123 on 2007-11-09
what are the keys for zoom in and out

---

### Post by forestpixie on 2007-11-10
I think what you want is enhanced zoom desktop in the advanced desktop settings - ccsm in a terminal if you like.
go to enh desk zoom in there, then click actions andthen zoom movement and you can configure away - I'd make a note of what you did just in case you want to change it back.

I could however, be completely wrong and that's not what you want - only be using this compiz stuff for a week or two myself.

---

### Post by playme123 on 2007-11-10
nah just want to know what keys you use to zoom in and zoom out

---

### Post by Forlong on 2007-11-10
The cube zooms automatically while rotating:

[Ctrl]+[Alt]+[Left Mousebotton] - hold the mouse and move it around

---

### Post by forestpixie on 2007-11-10
sorry

---

