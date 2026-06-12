---
title: "Compiz Fusion install issue"
date: 2007-12-29
forum: Desktop Effects &amp; Customization
---

### Post by Apples123 on 2007-12-29
Im Very new to Ubuntu and i like it alot however i really want compiz 

I looked at this link 

[https://help.ubuntu.com/community/CompositeManager/CompizFusion#head-1447dbabe59744a63cad770f4d2143fb45cb4aad](https://help.ubuntu.com/community/CompositeManager/CompizFusion#head-1447dbabe59744a63cad770f4d2143fb45cb4aad)

But after typing sudo apt-get install compiz compizconfig-settings-manager 

it said 

Reading package lists... Done
Building dependency tree
Reading state information... Done
compiz is already the newest verson.
E: Couldn't find package compizconfig-settings-manager

Im sorry if this is a really simple answer but its driving me crazy 

p.s. thanks in advance

---

### Post by billgoldberg on 2007-12-29
In ubuntu 7.10, compiz fusion is installed by default (not in 7.4)

But you will need an extra package to use it in all its glory.

Go to synaptic package manager (system --> administration). Press the search button, and type in compizconfig. Download and install that (click the little box next to its name and then the apply button on the top of the screen).

You can now tweak its setting in: system --> preferences -> advanced desktop effects settings

---

### Post by overdrank on 2007-12-29
> **Apples123 said:**
> Im Very new to Ubuntu and i like it alot however i really want compiz 

I looked at this link 

[https://help.ubuntu.com/community/CompositeManager/CompizFusion#head-1447dbabe59744a63cad770f4d2143fb45cb4aad](https://help.ubuntu.com/community/CompositeManager/CompizFusion#head-1447dbabe59744a63cad770f4d2143fb45cb4aad)

But after typing sudo apt-get install compiz compizconfig-settings-manager 

it said 

Reading package lists... Done
Building dependency tree
Reading state information... Done
compiz is already the newest verson.
E: Couldn't find package compizconfig-settings-manager

Im sorry if this is a really simple answer but its driving me crazy 

p.s. thanks in advance

Hi and welcome, 7.04 Feisty does come with desktop effects installed
[https://wiki.ubuntu.com/7.04Tour#head-72e463e7c61a66c61b567f361d2ad3fe38af39f8](https://wiki.ubuntu.com/7.04Tour#head-72e463e7c61a66c61b567f361d2ad3fe38af39f8)
And 7.10 does also. You may have to enable extra repos to install CCSM 
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
And you will have a graphics card to support the effects. Have you installed the drivers for your graphics card and what is the model?

---

### Post by Apples123 on 2007-12-29
> **billgoldberg said:**
>  Press the search button, and type in compizconfig. Download and install that (click the little box next to its name and then the apply button on the top of the screen).
You can now tweak its setting in: system --> preferences -> advanced desktop effects settings

it appears it has already been installed

---

### Post by Apples123 on 2007-12-29
> **overdrank said:**
> 
And you will have a graphics card to support the effects. Have you installed the drivers for your graphics card and what is the model?

That could be the next issue, where do i find drivers? i have a ASUS 7600GT

---

### Post by overdrank on 2007-12-29
> **Apples123 said:**
> That could be the next issue, where do i find drivers? i have a ASUS 7600GT

Hi and have you tried the restricted drivers located under system, administration. If this doesn't work to you liking you could try Envy script.
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by billgoldberg on 2007-12-29
> **Apples123 said:**
> That could be the next issue, where do i find drivers? i have a ASUS 7600GT

You could try:
System ->administratin -> restriced drivers manager

I installed my ati driver that way.

---

### Post by Apples123 on 2007-12-29
> **billgoldberg said:**
> You could try:
System ->administratin -> restriced drivers manager

I installed my ati driver that way.

Ive done that but it says driver

then nvidia accelerated graphics driver (latest cards) and the enabled box is not ticked

i tick it and it says enable the driver? i click enable driver and it then says the software source fore the package 

nvidia-glx-new 

is not inabled


Am i doing something wrong?

---

### Post by overdrank on 2007-12-29
> **Apples123 said:**
> Ive done that but it says driver

then nvidia accelerated graphics driver (latest cards) and the enabled box is not ticked

i tick it and it says enable the driver? i click enable driver and it then says the software source fore the package 

nvidia-glx-new 

is not inabled


Am i doing something wrong?

Hi and check the link I posted earlier about the repos and search synaptic manager for the nvidia-glx-new and install. Synaptic manager is located under system, administration. Good luck!

---

### Post by Forlong on 2007-12-29
> **Apples123 said:**
> Am i doing something wrong?
No, you didn't have access to the internet while installing. There's a bug that ticks off the sources you need now.

Go to *System &#8594; Administration &#8594; Software Sources* and check 'em (main, universe, restricted). Then reload and try again.

---

### Post by Apples123 on 2007-12-29
> **overdrank said:**
> Hi and check the link I posted earlier about the repos and search synaptic manager for the nvidia-glx-new and install. Synaptic manager is located under system, administration. Good luck!

Im using 7.10

'This page describes how to manage software repositories in Ubuntu 6.10 (Edgy Eft) and Ubuntu 6.06 (Dapper Drake)'

sorry i could be wrong but that doesnt help me?

What should i search in synaptic manager? nvidia-glx-new didnt show up with anything

---

### Post by Forlong on 2007-12-29
See my last posting in case you missed it. And install the driver only via *System &#8594; Administration &#8594; Restricted Drivers Manager*

---

### Post by Apples123 on 2007-12-29
> **Forlong said:**
> No, you didn't have access to the internet while installing. There's a bug that ticks off the sources you need now.

Go to *System &#8594; Administration &#8594; Software Sources* and check 'em (main, universe, restricted). Then reload and try again.

Your a genius! ok so now do i just start from the beginning aging?

---

### Post by Forlong on 2007-12-29
Now install/enable the driver in *System &#8594; Administration &#8594; Restricted Drivers Manager*
Then reboot and try ```
compiz
``` in a terminal. If it works, then you can install ccsm: ```
sudo apt-get install compizconfig-settings-manager
```
If not, post the output here.

---

### Post by Apples123 on 2007-12-29
haha the output well um i just restarted it and now the resolution is at 640x480 and it wont allow me to go any higher?

---

### Post by Forlong on 2007-12-29
Oh, that's not so good now, is it? :)

Try this
```
sudo dpkg-reconfigure xserver-xorg
```
and choose the proper resolution in the process.

Afterwards do this as well:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Reboot and see if it helped.

---

### Post by Apples123 on 2007-12-29
haha that worked 

so do i just do the 


Code:

compiz

in a terminal. If it works, then you can install ccsm:
Code:

sudo apt-get install compizconfig-settings-manager

??

---

### Post by Forlong on 2007-12-29
Yup, and if it fails, post the output. :)

---

### Post by Apples123 on 2007-12-29
um having an issue with all the windows sticking to the main panel. none of them have close, maximise or minimise options

---

### Post by Apples123 on 2007-12-29
heres the output

apples@apples-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:0391 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present.

---

### Post by Forlong on 2007-12-29
Is that the whole output? Because it should start a window decorator with it.

Try running ```
gtk-window-decorator
```


P.S. did you do the nvidia-xconfig command I posted earlier?

---

### Post by Apples123 on 2007-12-29
yea i did the nvidia config thing

then i did gtk widows decorator and it said it wasn't installed so i installed it with the command sudo apt-get install compiz and it appears to have been successful

---

### Post by Apples123 on 2007-12-29
Where do i go from here im pretty lost now:)

---

### Post by overdrank on 2007-12-29
> **Apples123 said:**
> Where do i go from here im pretty lost now:)

Ok so you have your minimize and close buttons back right and have you tried to activate compiz
with the alt, F2 keys and then enter ```
compiz --replace
```
I am not as good as Forlong but will try to help.

---

### Post by Apples123 on 2007-12-29
yea ive done that thanks um the screen cleared for a bit then went back to normal?

not sure whats ment to have happened

---

### Post by Apples123 on 2007-12-29
> **overdrank said:**
> Ok so you have your minimize and close buttons back right and have you tried to activate compiz
with the alt, F2 keys and then enter ```
compiz --replace
```
I am not as good as Forlong but will try to help.

Hey um im still missing minimize and close buttons

---

### Post by overdrank on 2007-12-29
> **Apples123 said:**
> Hey um im still missing minimize and close buttons

Ok could you post the output of this command in the terminal
```
cat /etc/X11/xorg.conf
``` you can use the code tags # and insert the text by copy and paste.

---

### Post by Apples123 on 2007-12-29
```
apples@apples-desktop:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Wed Sep 12 14:29:17 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 65.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

apples@apples-desktop:~$ 
```

---

### Post by overdrank on 2007-12-29
> **Apples123 said:**
> ```
apples@apples-desktop:~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Wed Sep 12 14:29:17 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 65.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
[COLOR="Red"]Option "AddARGBVisuals" "True"[/COLOR]
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

[COLOR="Red"]Section "Extensions"
    Option         "Composite" "Enable"
EndSection[/COLOR]

apples@apples-desktop:~$ 
```

Ok the only thing I see that may help is what I have added to your xorg and highlighted red. You can add these to your xorg with the command ```
gksudo gedit /etc/X11/xorg.conf
``` then you can copy and paste to add them. The restart x with the ctrl, alt, backspace keys and hope it all works. [-o<

---

### Post by Apples123 on 2007-12-29
haha great the windows are all working got all the buttons back but now the resolution is 800x600 haha

---

### Post by overdrank on 2007-12-29
> **Apples123 said:**
> haha great the windows are all working got all the buttons back but now the resolution is 800x600 haha

Ok sorry, you should be able to reconfigure you xorg and get back
```
sudo dpkg-reconfigure -phigh xserver-xorg
``` That should get you back to the good resolution. Sorry I could not be of more help. :(

---

### Post by Apples123 on 2007-12-29
na you've been a great help haha its been a bit of 2 steps foward 1 step back

---

### Post by Apples123 on 2007-12-29
As requested before by Forlong i typed compiz

here's the outcome

```
apples@apples-desktop:~$ compiz
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 
```

---

### Post by Forlong on 2007-12-29
I reckon you did a "reset" of your xorg.conf again?
Then run this again as well:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```

---

### Post by Apples123 on 2007-12-29
```
apples@apples-desktop:~$ sudo nvidia-xconfig --add-argb-glx-visuals -d 24
[sudo] password for apples:

Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Default Screen".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

what next?

---

### Post by Forlong on 2007-12-29
Restart X (or reboot) and pray that the resolution will be right this time :)
If not, post the output of ```
grep -v ^# /etc/X11/xorg.conf
```

If everything's OK, try ```
compiz
``` in a terminal again and if there's an error, post it... again.

---

### Post by Apples123 on 2007-12-29
um the resolution is fine but i have lost all close, maximise and minimise icons around the windows which is what i fixed before. the outcome of compiz

```
apples@apples-desktop:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 05:00.0 0300: 10de:0391 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

```

---

### Post by Forlong on 2007-12-29
Let's have a look at your xorg.conf again: ```
grep -v ^# /etc/X11/xorg.conf
```

---

### Post by Apples123 on 2007-12-29
```
apples@apples-desktop:~$ grep -v ^# /etc/X11/xorg.conf


Section "ServerLayout"

    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"                # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce 7600 GT]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce 7600 GT]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

---

### Post by Apples123 on 2007-12-29
um ive got compiz working and the cube etc works however i cant move windows (drag them) any ideas?

---

### Post by meindian523 on 2007-12-29
@Forlong

Is there a case against using Xgl for desktop effects?I guess that's what's required here.

---

### Post by Forlong on 2007-12-30
> **Apples123 said:**
> ```

    SubSection     "Display"
        Depth       24
**        Modes      "nvidia-auto-select"**
    EndSubSection

```
Nice, never seen that before. But maybe gtk-window-decorator doesn't work with that.
What was the resolution you want to use again?


@meindian523: there's no Xgl involved here. Only ATI cards that use the proprietary fglrx driver need it.

---

### Post by meindian523 on 2007-12-30
I asked because whenever the OP tries compiz,it's looking for Xgl and not finding it...so I thought we might as well give it what it wants? :) ;-)

---

### Post by Forlong on 2007-12-30
Ah, OK. No, the script doesn't "want" that, it just checks what's there in order to start Compiz properly.

---

### Post by Apples123 on 2007-12-30
the resolution is fine its 1280x1024

the only issue im having now is that i cant drag windows around on the workspaces although i still have the box's around the windows (close minmise maxmise)

---

### Post by Apples123 on 2007-12-31
um i have windows around some appalcations but not others for example i have them around pidgen and firefox but not when i open folders and i cant move any of them

---

### Post by Apples123 on 2007-12-31
i just did

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```\

and now i have all the windows, the only issue remaining is that i cant move windows around on work spaces

help any1?

---

### Post by Forlong on 2007-12-31
I thought you already did that...

So do you have window boarders now (the titlebars with max-/minimize and close)?

---

### Post by Apples123 on 2007-12-31
sure do i just cant move the windows around (they all seem to be stuck to the top bar)

---

