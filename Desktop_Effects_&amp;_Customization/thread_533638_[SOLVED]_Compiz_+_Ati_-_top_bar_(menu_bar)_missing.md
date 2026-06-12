---
title: "[SOLVED] Compiz + Ati - top bar (menu bar) missing"
date: 2007-08-24
forum: Desktop Effects &amp; Customization
---

### Post by bmdavis on 2007-08-24
Actually got Compiz Fusion working on a Dell Inspiron 6400 with ATI x1400 (Ubuntu Feisty)!  Wanted to post exactly how I did it after 3 days on this forum, but I can't even trace my own steps now. Maybe someday I'll post it...

Anyways, the ONLY problem I'm now experiencing (only 'so far'), is that the top menu bar is missing on all my windows.  Have searched for what to do throughout this forum, but nothing has worked for me. If I load the Beryl Manager and switch over to Beryl, the window reappears. It is only when I'm running Compiz that the menu bar disappears.    Any other ideas or posts that I haven't tried? 

tried the below command, here's what I got --

$ compiz --replace -c emerald &
[1] 11642

$ GConf backend: There is an unsupported value at path /apps/compiz/plugins/water/allscreens/options/toggle_rain_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/water/allscreens/options/toggle_wiper_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/cube/allscreens/options/unfold_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/cube/allscreens/options/next_slide_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/cube/allscreens/options/prev_slide_key. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/rotate/allscreens/options/initiate_button. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

For some reason I can't disable the "Gconf backend" and switch to FlatFile. Strange, but there it is.  

Again, I'm very happy with how everything else is working.  If I have to switch to Beryl to get back my top bar, so be it.... but it would be nice to fix it!

Thanks guys for all the help...

---

### Post by captainwitherspoon on 2007-08-26
Hey, I've been having the same problem. I removed some extra plugin packages and the problem was solved, when I find out exactly which package was causing the problem I'll let you know...

---

### Post by captainwitherspoon on 2007-08-26
I had to rerun envy and reinstall compiz, it's working now. good luck!

---

### Post by bmdavis on 2007-08-27
Yeah, would love to know what plugins you took off.

Can't redo envy - that's what messed my screen up in the first place!  ;-)   Anyways, will keep playing around.  The "SMART" window placement in compiz can't be disabled, which is funny...

---

### Post by captainwitherspoon on 2007-08-29
I went to synaptic and searched for compiz and removed everything. Then I removed my compiz directory and reinstalled everything. It worked for a while but I have since screwed it up and now I'm back with the same problem you have. 

Can anyone help? compiz looks really sweet but i can't use it without title bars!!!

---

### Post by Inxsible on 2007-08-29
To get the window borders back you need to open a terminal and type in ```
metacity --replace
```Of course this means that you are running metacity and not Compiz.

Also the command ```
compiz --replace
``` needs to run in the Alt +F2 window dialog, NOT the terminal

---

### Post by Inxsible on 2007-08-29
> **captainwitherspoon said:**
> I went to synaptic and searched for compiz and removed everything. Then I removed my compiz directory and reinstalled everything. It worked for a while but I have since screwed it up and now I'm back with the same problem you have. 

Can anyone help? compiz looks really sweet but i can't use it without title bars!!!
Try [this]("http://ubuntuforums.org/showthread.php?t=533201") once to remove everything related to Compiz. I know you already tried it thru Synaptic, but you might have missed a few packages

---

### Post by Inxsible on 2007-08-29
> **bmdavis said:**
> Actually got [COLOR=Red]Compiz Fusion[/COLOR] working on a Dell Inspiron 6400 with ATI x1400 (Ubuntu Feisty)!  Wanted to post exactly how I did it after 3 days on this forum, but I can't even trace my own steps now. Maybe someday I'll post it...

Anyways, the ONLY problem I'm now experiencing (only 'so far'), is that the top menu bar is missing on all my windows.  Have searched for what to do throughout this forum, but nothing has worked for me. If I load the Beryl Manager and switch over to [COLOR=Red]Beryl[/COLOR], the window reappears. It is only when I'm running [COLOR=Red]Compiz [/COLOR]that the menu bar disappears.    Any other ideas or posts that I haven't tried? 

Again, I'm very happy with how everything else is working.  If I have to switch to [COLOR=Red]Beryl [/COLOR]to get back my top bar, so be it.... but it would be nice to fix it!

Thanks guys for all the help...
Having Compiz Fusion and Beryl both installed has given a lot of grief to many.  You might want to uninstall Beryl and Compiz Fusion completely and then re-install Compiz Fusion.

This may or may not work though. See my above post on how to completely remove Compiz Fusion, if you are willing to go that route.

The best thing is, if it still doesn't work, you can always install Beryl again :)

---

### Post by captainwitherspoon on 2007-08-29
Hey, thanks for the reply. I've seen that exact post and tried it a few times. Lately compiz comes up with title bars but they can't be moved and if I open new programs they don't have title bars. I had it working for a while but I screwed it up and the instructions in that post don't change back whatever I changed. 

Here's my xorg.conf
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

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
    Identifier     "NEC E950"
    Option         "DPMS"
EndSection

Section "Device"

# from https://bugs.launchpad.net/fedora/+source/compiz/+bug/89741
    Identifier     "nVidia Corporation NV36 [GeForce FX 5700LE]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV36 [GeForce FX 5700LE]"
    Monitor        "NEC E950"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "XAANoOffscreenPixmaps" "true"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1440" "1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

One thing that might be a clue, when I switch back to metacity I get 
```
z@xZx:~$ metacity --replace
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```
That error wasn't there before, not sure what it means...

---

### Post by captainwitherspoon on 2007-09-01
I solved this. I ran this tutorial 
[http://ubuntuforums.org/showthread.php?t=536149&highlight=install+compiz+fusion](http://ubuntuforums.org/showthread.php?t=536149&highlight=install+compiz+fusion)
and it worked. Also, I was running compiz -- replace in a terminal and closing the terminal (duh) which was causing problems.

---

### Post by bmdavis on 2007-09-10
Thanks much!  Played around, uninstalled Beryl and Metacity, then followed this post (see bottom). 

[http://ubuntuforums.org/showthread.php?t=54580](http://ubuntuforums.org/showthread.php?t=54580)

Solved!

---

