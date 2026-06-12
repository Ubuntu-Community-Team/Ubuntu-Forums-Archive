---
title: "XPS M1330 - Problems with Ubuntu GUSTY 7.10 : NVIDIA drivers"
date: 2007-11-08
forum: Dell  Ubuntu Support
---

### Post by hikcygrek on 2007-11-08
Hi,
I have a XPS M1330 with NVIDIA 8400 GS.

All the install done, all work fine except my NVIDIA card.

I use the the proprietary driver like they said at ubuntu-fr for this laptop.
, install it, but when i restart the computer, the X server does'nt keep this new setting...
He still use VESA and don't know which screen to use...

I also tried using restricted drivers interface but it's the same, does'nt work after reboot.

Do you have any idea?

---

### Post by pbcartwright on 2007-11-08
try installing envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
it should setup your nvidia card. It worked on my XPS M140 laptop and desktop.

---

### Post by hikcygrek on 2007-11-08
hello pbcartwright, i go trying this ...

---

### Post by hikcygrek on 2007-11-08
Ok, that's done.

ENVY installed the NVIDIA driver correctly. And after restart settings still here for the video card. So i can use

But, my screen resolution problem still here: each start x server use 1024x768 and no 1280x800.

Even if set it using the displayconfig-gtk after restart the problem still here.

I don't know why?

I don't know if it's important or not but since the beginig of my gusty's install i have no splash when boot time... instead off i have black screen.

---

### Post by Dellfan on 2007-11-09
One of the common causes of no splash is having a messed up resolution. Check the resolution set in  /etc/usplash. Set it to the correct resolution and then run the command:

sudo dpkg-reconfigure usplash

Another cause is incorrect settings in /boot/grub/menu.lst. If /etc/usplash looks ok, take a look at this post:

[http://ubuntuforums.org/showthread.php?t=317888&highlight=no+splash+screen+while+booting]("http://ubuntuforums.org/showthread.php?t=317888&highlight=no+splash+screen+while+booting")

The incorrect resolution is most likely due to settings in /etc/X11/xorg.conf. Ensure that you have a 1280x800 resolution called out. If you need help editing your xorg.conf, please post a copy of it.

---

### Post by hikcygrek on 2007-11-09
Hi Dellfan,
Thanks for your advices :)

For my boot resolution  problem i solved it.

To do this I:

-> ran the nvidia-setting gui with admin access,

-> then i configured in  "x server display configuration" section the right resolution 1280x800 / 60Hz

->  and then save the conf using the "Save to X configuration file" button

-> And clean up the /etc/X11/xorg.conf with just the conf i want ...

For my splash problem, it still here, i am trying what you said.

Thanks.

---

### Post by hikcygrek on 2007-11-10
Hi, 
I tried to configure
 /etc/usplash.conf then dpkg-reconfigure usplash
/boot/grub/menu.lst then update-grub

with the right conf but it does'nt work...

In fact, after i modified the menu.lst and then used the update-grub command, the changes did'nt take effect

---

### Post by Dellfan on 2007-11-10
Could you provide more details around "changed didn't take effect"? Do you mean the file did not save, or the changes you made did not have the effect you were expecting?

Could you post your menu.1st file please. Note that "update-grub" just inserts a list of installed kernels in the grub config file. It may have undone the changes you made and put the default options back into menu.1st, depending on how you ran it. If you are directly editing menu.1st you do not need or want to run update-grub after.

---

### Post by maysala on 2007-11-10
Hi

I-m having the same problems. Have sucessfully installed the nvidia driver with envy, but dont have in my xorg.conf the 1280x800 option. As I dont quite understand the parameters, didnt manually change the file... My screen is running in the lcd 1440x1050 generic, the only one that gives me the option of 1280x800 definition...

How could I update the xorg.conf? what would be the right parameters? and wich monitor model should i choose? the generic should be alright?

thanks a lot

---

### Post by hikcygrek on 2007-11-10
Hi Dellfan (thanks for your patience:)
I meant i change directly the file menu.lst and the changes don't stay ...
It's because i ran update-grub .

So i tried several conf but it still does'nt work: i have no splash screen), 

that's my menu.lst now:

---

### Post by hikcygrek on 2007-11-10
Hi maysala,

For me after install the drivers using envy,
i chosen Generic Monitor in 1024x768 and set 1280x800 using the displayconfig-gtk interface.
Then, i ran in command line:
sudo nvidia-setting to set the resolution 1280x800 at 60hz in the "X server display configuration" section, then you valid using the "save to X configuration file" button.

then, i made a copy of my xorg.conf file, then  i cleaned the xorg.conf file deleting the defaults options.

Now my xorg.conf is like this:

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder26)  Thu Oct  4 10:49:07 PDT 2007

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Thu Oct  4 10:48:30 PDT 2007
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "fr"
    Option         "XkbVariant" "oss"
    Option         "XkbOptions" "lv3:ralt_switch"
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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "AUO"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400M GS"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x800_60 +0+0; 1024x768@60 +0+0; 800x600@60 +0+0; 640x480@60 +0+0"
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

