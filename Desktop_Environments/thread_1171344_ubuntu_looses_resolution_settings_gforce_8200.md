---
title: "ubuntu looses resolution settings gforce 8200"
date: 2009-05-27
forum: Desktop Environments
---

### Post by paul_anders on 2009-05-27
Hi can some one throw me a life line 
thank you 

ubuntu reboots on a default screen resolution of 800x600. in order for 
me to get the correct settings i have to run "xrandr -s 1024x768" then the screen switches and shows correctly. at this point i confirm that xorg.conf has the correct details. as shown below
when i turn off the machine i have to redo the above procedure again.

my "Nvidia x server settings" shows correct details only after running xrandr.
im using proprietary nvidia accelerated graphics driver version 180
and i have all the updates too

here is another question. why does suse gets all my graphic cards bang on
point working (even before suse hooked up with microsoft) and why does the great ubuntu give problems with every graphic card i throw at it.
they both use linux kernel so whats the issue ?
and no i dont want to use Suse.

> 
my graphic card is "Nvidia GeForce 8200"
here is my working xorg.conf 
*****************************************************************
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
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

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "CRT-0"
    HorizSync       28.0 - 55.0
    VertRefresh     43.0 - 72.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    Option         "NoLogo" "True"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8200"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
EndSection

Section "Screen"

# Removed Option "metamodes" "1024x768 +0+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"

---

### Post by Murrquan on 2009-05-27
I'm not sure how to help with your configuration, but there *is* a way to run that command every time you start up!

Go to System -> Preferences -> Startup Applications. Then click "Add," and paste that command in where it says "Command." (You might want to name it and comment it too, so that you'll know what it is later on.)

That should keep you from having to manually enter the command every time you log in!

---

### Post by paul_anders on 2009-05-27
Murrquan
Thank you so much... i have been here thinking along the same lines but i was messing around with the gdm.conf till i messed up something then all went tits up....

thanks again for the work around solution.

i just wish that bunty could sort screen issues like Suse. if this could 
be done then bunty would be 100%

none the less though thanks

PA

---

