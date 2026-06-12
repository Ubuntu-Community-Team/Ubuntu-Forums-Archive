---
title: "nvidia woes"
date: 2006-10-03
forum: Gaming &amp; Leisure
---

### Post by Josey on 2006-10-03
I have been having trouble getting descent 3 to run.
I'll run the game in the same resolution as my desktop but the game will be in the middle pretty small with alot of black around it. The game claims it's still in the same resolution.
I hit new game and pick a mission. The mission loads and then crashes me back to the desktop. If I run it through terminal I get some glx errors saying nvidia isnt installed right..

So I have been trying to install nvidia correctly and through trial and error I have found that the way to get descent 3 to work perfectly is to boot into recovery mode and then use 'startx' to get into xubuntu gui.

I use the same launcher as I do in the normal boot.
I load the game that way and it works perfect.
This is one of the first games I've got loaded on here and I'm impressed. It runs better than it did in XP when I get it running. :)

Anyway... if I boot normally I'm back to a small game screen and crashes.
I'm sure the problem is in my xorg.conf but I'm pretty lost as this is my 2nd week in linux. 

I haven't modified anything really after running 'sudo aptitude install nvidia-glx'

Any idea's why recovery mode would be better for nvidia-glx I guess is my question here. :)

Any help is apriciated.

---

### Post by Perfect Storm on 2006-10-03
```
cat /etc/X11/xorg.conf
```

---

### Post by Josey on 2006-10-03
Here is the error I get when the game crashes when running from terminal.

```
X Error of failed request:  GLXBadContextTag
  Major opcode of failed request:  147 (GLX)
  Minor opcode of failed request:  144 ()
  Serial number of failed request:  2137
  Current serial number in output stream:  2138

```

---

### Post by Josey on 2006-10-03
xorg.conf

```
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
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
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
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "KDS VS-7blk"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV20 [GeForce3 Ti 200]"
    Monitor        "KDS VS-7blk"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

---

### Post by Josey on 2006-10-03
If I do this nvidia works beautifully.
I remove nvidia-glx, log out of xfrce session and restart x server. 
Then I install nvidia-glx from terminal then startx everything is perfect. 
It runs like a gem if I don't have nvidia-glx running on a normal boot. I just don't get it. What changes?

---

### Post by Josey on 2006-10-04
After some digging it seem i might have something else thats running using opengl or oss and theres a conflict. :-k 

Anyone have any ideas for me? :confused:

---

### Post by Josey on 2006-10-04
It seems my problem was xserver-xgl. Running this and gaming seems to be a bad idea.

Also had to fix /ect/gdm/gdm.conf-custom and remove xgl options so I could get something other than terminal at boot up. In the future it might be a good idea to have packages like xserver-xgl edit the xgl options out of gdm.conf-custom so it doesn't break the boot manager when removed.

For anyone else that might be reverting back from xserver-xgl and are having trouble loading gdm...
```

sudo gedit /ect/gdm/gdm.conf-custom
delete this under [servers]

 0=Xgl
 
 [server-Xgl]
 name=Xgl server
 command=/usr/bin/Xgl -fullscreen -br -accel xv:fbo -accel glxbuffer
 flexible=true

```

---

