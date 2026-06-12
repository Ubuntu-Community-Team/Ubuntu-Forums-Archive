---
title: "Beryl Assistance"
date: 2007-04-24
forum: Desktop Effects &amp; Customization
---

### Post by xflatlinex on 2007-04-24
I have installed Beryl on Ubuntu 64 7.04 and have started up the Emerald Themr 0.2.1.  
My question is, when I select a theme in the Emerald Windows, should it automatically apply that them for me?  Maybe I am doing this all wrong.
Thanks in Advance.

---

### Post by xtreme35967 on 2007-04-24
Yes it will do it automatically.

---

### Post by xflatlinex on 2007-04-24
very strange indeed. I am clicking and double clicking on each of the installed themes in Emerald Themer and I get no results, as in it does nothing. Any suggestions?
Thanks

---

### Post by xtreme35967 on 2007-04-24
I had to edit one of the files on my computer to get it to work correcty. I will have to see if I can find the forum post that I got the information from.

---

### Post by xtreme35967 on 2007-04-24
There is some lines that you need to add into your xorg.conf file under the "devices" section.

Here are the lines you need to add.

append the following to your /etc/X11/xorg.conf in the “Device” section:

Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"

I had this same issue. I found this info in a Beryl link but it worked for me.

---

### Post by xflatlinex on 2007-04-24
Cool, I will try it once I get home and will post the results.

> **xtreme35967 said:**
> There is some lines that you need to add into your xorg.conf file under the "devices" section.

Here are the lines you need to add.

append the following to your /etc/X11/xorg.conf in the “Device” section:

Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"

I had this same issue. I found this info in a Beryl link but it worked for me.

---

### Post by xflatlinex on 2007-04-24
Xtreme,
I tried adding those lines and it still didnt work any other suggestions?

---

### Post by srhlefty on 2007-04-24
this is a dumb question, but is Beryl Manager running, and is the window manager set to Beryl?

---

### Post by xflatlinex on 2007-04-24
> **srhlefty said:**
> this is a dumb question, but is Beryl Manager running, and is the window manager set to Beryl?

Lol May not be a dumb questions, I have it open via the command "beryl" but do not have the icon in my bar.  And how would I set the window manager to beryl?  Sorry, im still kinda a newbie. thanks for the patience

---

### Post by srhlefty on 2007-04-24
the command to start beryl is

beryl-manager

and if it's working then you'll hear your graphics card's fan spin up, and the icon should also show up

---

### Post by srhlefty on 2007-04-24
then if you right click on the icon, one of the choices is Emerald Theme Manager, I believe

---

### Post by xflatlinex on 2007-04-24
> **srhlefty said:**
> the command to start beryl is

beryl-manager

and if it's working then you'll hear your graphics card's fan spin up, and the icon should also show up


I have the icon now in the sys tray and when I select Beryl as the window manager the screen just flashes a few times and doesnt do anything.  When I check to see if the window manager has changed, it doesnt change. it just stays at Metacity

---

### Post by srhlefty on 2007-04-24
That means beryl is crashing.  I don't know how to fix it, sorry.

---

### Post by kbzona on 2007-04-24
When you choose a theme click it..  after that right click beryl icon and click where it says RELOAD WINDOWS DECORATOR.... if this doesnt work  then ur beryl is screwed up

---

### Post by xflatlinex on 2007-04-24
> **kbzona said:**
> When you choose a theme click it..  after that right click beryl icon and click where it says RELOAD WINDOWS DECORATOR.... if this doesnt work  then ur beryl is screwed up

Ok, that didnt work either but here is the output of some errors.  Any Ideas?

* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
/usr/bin/compiz.real: No composite extension
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
Reloading...
Reloading...

---

### Post by kbzona on 2007-04-24
Check that ur xorg.conf has enabled the composite extension

also mmm try adding this to Xorg.conf in the "Device" section:

Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"

---

### Post by srhlefty on 2007-04-24
> Checking for XComposite extension : failed
That's why beryl is crashing.  I'm not sure if XComposite is something in the driver, or a separate package that wasn't properly downloaded/installed

---

### Post by xflatlinex on 2007-04-24
> **kbzona said:**
> Check that ur xorg.conf has enabled the composite extension

also mmm try adding this to Xorg.conf in the "Device" section:

Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"

Can you tell me how to check to see if my xorg.conf has enabled the composite extension.  Btw: i also get the error "the composite extension is not available" when i go to system-->desktop effects

---

### Post by kbzona on 2007-04-24
in the console type:

sudo gedit /etc/X11/xorg.conf

also Under Section "Module", make sure that the following lines are included, and add them if they are not:

Load "dri"
Load "vbe"
Load "glx"

also add this in the end if isnt there already...:

Section "DRI"
        Mode 0666
EndSection

Finally try to add this at the end too:

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "on"
EndSection

---

### Post by xflatlinex on 2007-04-24
> **kbzona said:**
> in the console type:

sudo gedit /etc/X11/xorg.conf

also Under Section "Module", make sure that the following lines are included, and add them if they are not:

Load "dri"
Load "vbe"
Load "glx"

also add this in the end if isnt there already...:

Section "DRI"
        Mode 0666
EndSection

Finally try to add this at the end too:

Section "Extensions"
        Option  "Composite" "Enable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "on"
EndSection

Ok, I added some of that and now when I start up Beryl-manager I am getting the following. I am not sure if it was there before or not.

josh@jgwUbuntu:~$ beryl-manager
josh@jgwUbuntu:~$ Xlib:  extension "XFree86-DRI" missing on display ":0.0".

josh@jgwUbuntu:~$ **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

---

### Post by xflatlinex on 2007-04-24
Can someone please tell me the easist way to uninstall Beryl and Beryl Manager
THanks

---

### Post by xflatlinex on 2007-04-25
Wow, I just watched a video of Beryl in action and SO WISH i could get it to work properly.

---

### Post by YourBabysDaddy on 2007-04-26
I'm having trouble with my Nvidia 7900GS. I had beryl working perfectly, then one day it decided to start crashing on me. It keeps switching back to metacity automatically. Here's what I got when I tried to run beryl:

```
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options
Not a JPEG file: starts with 0x47 0x49
```

I don't know what the last line means, but i think that's my problem.

---

