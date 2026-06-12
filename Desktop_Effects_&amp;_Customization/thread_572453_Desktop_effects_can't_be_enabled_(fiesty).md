---
title: "Desktop effects can't be enabled (fiesty)"
date: 2007-10-10
forum: Desktop Effects &amp; Customization
---

### Post by fourthdimension on 2007-10-10
Hey All

I found a few similar threads, but none matched my case close enough, so I decided to start a new one.  OK, I tried to install compiz fusion once before and somehow the install failed and everything related to compiz was messed up.  I did my best to fix it and installed again using a guide from these forums, and things went well enough, but when I try to enable the desktop effects, it says they couldn't be enabled.  I tried to enable them through the terminal to see what was happening, and it says:

```
my_machine:~$ desktop-effects
nvidia restricted driver is already enabled
Checking for Xgl: gtk-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0111 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

I also noticed that my update manager tells me I can update "compiz-core (version 1:0.5.2+git20070918-0ubuntu5~ppa1)"  to "1:0.5.2+git20070918-0ubuntu5~ppa1", but no matter how many times I download and install the update (through both the update manager and the terminal), it doesn't take effect and the manager asks me to update it again.  The terminal gives no errors, and I've restarted my system.  I have the restricted nvidia driver enabled, and my system has previously supported beryl (though not on this install - the title bars disappeared, which is why I wanted to install compiz fusion).

Did the failed first install mess my system up so badly that the only course is to reinstall feisty, or is there another way to fix these problems?

Thanks.

---

### Post by Rupertronco on 2007-10-10
If you installed compiz fusion then you're going about starting it the wrong way. Hit Alt+f2 and type "compiz --replace". The old desktop effects button is for the original compiz, not compiz fusion. I'm assuming you're in feisty and used Amaranth's repository, the update bug is a known issue, don't worry about it. 

Try the "compiz --replace" then post what happens. Also type "ccsm" in a terminal or run box to see the settings manager and check out the keybindings.

---

### Post by fourthdimension on 2007-10-10
I see.  How do I enable the effects with compiz fusion, then?
I ran compiz --replace earlier, but the screen blinked and nothing happened.  
I checked out the key bindings, but they're all default.  Am I looking for something in particular?
Thanks for the help.

---

### Post by FuturePilot on 2007-10-10
First we need to get rid of that toggle_shaded error
Press Alt+F2 and type in ```
gconf-editor
```
Navigate to Apps>Metacity>window_keybindings 
The second from the bottom should say
toggle_shaded and the value should be blank, which is the problem. It needs to say
```
disabled
``` So change it to disabled

Now for this
```
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 
```
A bit more complicated. I recommend proceeding with a bit of caution here. Your card has less than 64MB of VRAM, which means you will get hit big time with the black window bug. I believe the latest Nvidia driver has improved on this. To see what driver you have do this
```
cat /proc/driver/nvidia/version
``` 
You need the 9643 driver if you have an older card or the 100.14.19 driver if you have a newer card. You can get the latest driver easily with [Envy]("http://albertomilone.com/nvidia_scripts1.html") It will automatically give you the correct driver for your card. When it asks you to configure xorg.conf say No. If you install the driver with Envy you will have to run Envy after a kernel update because X will break. So when you get a kernel update reboot after installing it, X will fail, but that's ok, login through the terminal and run Envy
```
sudo envy -t
```

Now to get around the 64MB limit we need to do a little hack
```
gksudo gedit /usr/bin/compiz
```
Find the section near the top that looks like this
```
# Minimum amount of memory (in kilo bytes) that nVidia cards need 
# to be allowed to start 
# Set to 262144 to require 256MB
NVIDIA_MEMORY="65536" # 64MB 
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default
```
Now make it look like this. The red is what has been added and changed
```
# Minimum amount of memory (in kilo bytes) that nVidia cards need 
# to be allowed to start 
# Set to 262144 to require 256MB 
[COLOR="Red"]# Set to 30000 to hack around 64MB minimum limit 
# Set to 65536 to revert back to 64MB (default)[/COLOR]
NVIDIA_MEMORY="[COLOR="Red"]30000[/COLOR]" # [COLOR="Red"]32MB [/COLOR]
NVIDIA_SETTINGS="nvidia-settings" # Assume it's in the path by default
```
Save and try starting Compiz now.
```
compiz --replace
```
Note that you will have to edit this file again after a Compiz update since it gets overwritten.

---

### Post by Forlong on 2007-10-10
> **FuturePilot said:**
> Note that you will have to edit this file again after a Compiz update since it gets overwritten.
Or you just run Compiz with
```
SKIP_CHECKS=yes compiz
```
then you won't need to change /usr/bin/compiz at all.

---

### Post by fourthdimension on 2007-10-10
I followed the last two posts completely, and I got this:

```
my-machine:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0111 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
my-machine:~$ SKIP_CHECKS=yes compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0111 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for nVidia: present. 
Checking for FBConfig: Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
not present. 
SKIP_CHECKS is yes, so continuing despite problems.
Checking for Xgl: not present. 
Starting emerald
Xlib:  extension "GLX" missing on display ":0.0".
/usr/bin/compiz.real (core) - Fatal: Root visual is not a GL visual
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0


```

I wonder what that "not present" stuff is all about.

---

### Post by mjwood0 on 2007-10-10
Could you post the output of:
```
cat /etc/X11/xorg.conf
```

It sounds like you need the glx module to be loaded.

---

### Post by fourthdimension on 2007-10-10
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Nov  9 17:55:20 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

        # path to defoma fonts
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/usr/share/fonts/X11/cyrillic"
    FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath        "/usr/share/fonts/X11/Type1"
    FontPath        "/usr/share/fonts/X11/100dpi"
    FontPath        "/usr/share/fonts/X11/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "vbe"
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
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "EV700"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV11DDR [GeForce2 MX200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV11DDR [GeForce2 MX200]"
    Monitor        "EV700"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

---

### Post by FuturePilot on 2007-10-10
You got some stuff in the wrong sections
Move these 3 lines to the Device section. They are currently in your Screen section.
```
Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
```
Logout and restart X. (Ctrl+Alt+Backspace)
> **Forlong said:**
> Or you just run Compiz with
```
SKIP_CHECKS=yes compiz
```
then you won't need to change /usr/bin/compiz at all.
True but then it makes it more complicated to have it start when you login.

---

### Post by fourthdimension on 2007-10-10
Thanks.  I moved them and restarted X.  When I ran compiz --replace I got this:
```
my-machine:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0111 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

---

### Post by FuturePilot on 2007-10-10
> **fourthdimension said:**
> Thanks.  I moved them and restarted X.  When I ran compiz --replace I got this:
```
my-machine:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0111 (rev b2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

Try adding this to the very bottom of xorg.conf
```
Section "Extensions"
Option "Composite" "Enable"
EndSection
```
Restart X again

---

### Post by fourthdimension on 2007-10-11
Hmm.  Seems like I just get the same error again...

---

### Post by FuturePilot on 2007-10-11
What's the output of 
```
cat /proc/driver/nvidia/version
```

---

### Post by fourthdimension on 2007-10-11
```
NVRM version: NVIDIA Linux x86 Kernel Module  96.43.01  Wed Sep  5 19:12:23 PDT 2007
GCC version:  gcc version 4.1.2 (Ubuntu 4.1.2-0ubuntu4)

```

---

### Post by FuturePilot on 2007-10-11
Hmmm. I'm not sure why it's not finding the texture_from_pixmap:confused:
Let's see what your glxinfo is
```
glxinfo
```

---

### Post by fourthdimension on 2007-10-11
```
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x5a 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None

```
Thanks for all your help so far.

---

### Post by FuturePilot on 2007-10-11
Hmmm. That could be a problem:o 
It looks like something didn't get installed right. You could try reinstalling the driver with Envy and see if it fixes that. If that doesn't work we're going to need to do it manually.
You can download it here
[http://www.nvidia.com/object/linux_display_x86_96.43.01.html]("http://www.nvidia.com/object/linux_display_x86_96.43.01.html")
And since we've already got all the dependencies installed from Envy, just logout and drop to a terminal (Ctrl+Alt+F2) then login. 
Stop X
```
sudo /etc/init.d/gdm stop
```
cd to the directory where you downloaded the driver to
```
cd /path/to/driver
```
Then run it
```
sudo sh NVIDIA-LINUX-whatever-its-called.run
```
Say No when it asks to configure xorg.conf
Start X again
```
sudo /etc/init.d/gdm start
```

Sorry if it seems like we're going in circles.;)

---

### Post by fourthdimension on 2007-10-12
Thanks.  That helped some - compiz starts now with only one error (xgl still isn't present).  I get a lot of these: ```
(emerald:16181): Wnck-WARNING **: Unhandled action type (nil)

```, but they haven't seemed to affect much so far.
Thanks for all the help!  You've been great.

---

### Post by FuturePilot on 2007-10-12
> **fourthdimension said:**
> Thanks.  That helped some - compiz starts now with only one error (xgl still isn't present).  I get a lot of these: ```
(emerald:16181): Wnck-WARNING **: Unhandled action type (nil)

```, but they haven't seemed to affect much so far.
Thanks for all the help!  You've been great.

You can ignore the error about XGL. Since you have a Nvidia card you don't need XGL. As for that Emerald error, I think that's normal. My .xsession-errors file is loaded with those. They don't seem to affect anything so you can probably ignore those as well. Glad everything is working.:D

---

### Post by fourthdimension on 2007-10-12
Thanks - I think that fixed everything.  Just one last question - how do I set compiz fusion and emrald to the default desktop/window managers so they'll stay open when the terminal's closed?

---

### Post by FuturePilot on 2007-10-12
That's possibly a draw back of Compiz. I've tried it on my laptop with a GeForce2 Go (32MB) and it did run very slow.:( Not much can be done about that

---

### Post by Forlong on 2007-10-12
> **fourthdimension said:**
> how do I set compiz fusion and emrald to the default desktop/window managers so they'll stay open when the terminal's closed?
Just run them via [Alt]+[F2] or add them to System &#8594; Preferences &#8594; Sessions &#8594; Startup Programs

---

### Post by fourthdimension on 2007-10-12
Thanks.  Turned out the speed problem fixed itself.  By the way, what's the name of the option that makes the windows stick to the edges of the screen?  I want to disable it, but I can't find it.  
OK, that's all!  Thanks a lot, everyone!

---

### Post by Forlong on 2007-10-12
> **fourthdimension said:**
> what's the name of the option that makes the windows stick to the edges of the screen?  I want to disable it, but I can't find it.
Disable the **Snapping Windows** plugin as well as **Wobbly Windows &#8594; General &#8594; Snap Inverted **

---

### Post by fourthdimension on 2007-10-12
Hmm...  I guess compiz just wants to act like that - that's what I tried first.  Well, at least I was on the right track! lol
Remember when I said "That's all"?  I lied.  I have one more problem (but by now you're probably thinking "this kid has problems in general!) :lolflag:  Sorry.
When I open a program, the file and title bars start under the taskbar, and if I hide the taskbar, the window moves up.  I can't move the windows by shortcut keys or the right click menu, and I've disabled the wobbly windows and snapping windows.  Is this a misconfiguration or just a glitch with my system?
Thanks.

---

### Post by FuturePilot on 2007-10-12
Do you still have the Move Windows plugin enabled? I'm not sure if that is responsible for your problem or not. Or maybe it's the Place Windows plugin. I'm not sure.

---

### Post by Forlong on 2007-10-13
My guess would be the Move Window plugin too.

And set the **Placement Mode** in the also mentioned Place Windows plugin to **Smart**.

---

