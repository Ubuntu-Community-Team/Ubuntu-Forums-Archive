---
title: "problems w/ compiz fusion... no borders w/ nvidia"
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by pjones0404 on 2007-07-01
i recently updated to feisty and tried to install compiz fusion. it installed w/ out errors but i do no have windows borders. how can i fix this? i also get a white screen when opening applications. 

iBeryl ran fine when i had edgy installed.

---

### Post by hyperair on 2007-07-01
You upgraded to Feisty eh? Perhaps you might have had your xorg.conf overwritten. Run this command:
```

sudo nvidia-xconfig --add-argb-glx-visuals

```
in the terminal and restart your X server.

---

### Post by fjf on 2007-07-01
I have the same problem, no window decorations and empty terminal window on feisty.  None of the threads here has helped me.  Maybe we should just wait until this thing is more stable.

---

### Post by steveneddy on 2007-07-01
> **fjf said:**
> Maybe we should just wait until this thing is more stable.

Compiz, Compiz-Fusion and Beryl are all Beta software and not guaranteed to work.

It takes some skill and set up time to get these types od desktop effects running correctly.

Try searching these forums.

[http://ubuntuforums.org/forumdisplay.php?f=223](http://ubuntuforums.org/forumdisplay.php?f=223)

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

[http://www.opencompositing.org/](http://www.opencompositing.org/)

[http://ubuntuforums.org/showthread.php?t=481314](http://ubuntuforums.org/showthread.php?t=481314)

---

### Post by autocrosser on 2007-07-01
I've been using Beryl for some time & just changed to Compiz-Fusion. After a small amount of experimenting, I found that if I reinstalled Emerald & called Compiz with: 

(code)  compiz --replace -c emerald --replace          

 Compiz will use Emerald as the window decorator & I could use all of my Beryl/Emerald themes I've collected.

Hope this helps:D

---

### Post by pjones0404 on 2007-07-01
> **hyperair said:**
> You upgraded to Feisty eh? Perhaps you might have had your xorg.conf overwritten. Run this command:
```

sudo nvidia-xconfig --add-argb-glx-visuals

```
in the terminal and restart your X server.


this fixed it for me. i appreciate it.

---

### Post by Bachstelze on 2007-07-01
> **pjones0404 said:**
> i recently updated to feisty and tried to install compiz fusion. it installed w/ out errors but i do no have windows borders. how can i fix this?

First, try to move a window by holding the Alt key and dragging it. If it works, that means Compiz is running and you can do :

```
gtk-window-decorator --replace &
```


***EDIT :** Oh, never mind, I guess I should read threads entirely before replying :D*

---

### Post by godog on 2007-07-05
> **hyperair said:**
> You upgraded to Feisty eh? Perhaps you might have had your xorg.conf overwritten. Run this command:
```

sudo nvidia-xconfig --add-argb-glx-visuals

```
in the terminal and restart your X server.

Worked for me too, thanks a lot! :D

---

### Post by JerMe on 2007-07-07
> **hyperair said:**
> You upgraded to Feisty eh? Perhaps you might have had your xorg.conf overwritten. Run this command:
```

sudo nvidia-xconfig --add-argb-glx-visuals

```
in the terminal and restart your X server.

Me three, thanks for the info!

---

### Post by hyperair on 2007-07-08
Well good to hear that it helped so many. ^^ Someone should make a sticky of some thread showing all the different solutions to the no window borders problem, as there seems to be a lot of these around.

---

### Post by rmflagg on 2007-08-06
Ok...I have tried everything that I could think of to get the window decorations to show up when running compiz-fusion.  I have tried so far:
compiz --replace
compiz --replace -c emerald
compiz --replace -c emerald --replace

I have beryl-manager, emerald installed.  I have altered the xorg.conf file and added the extra line to the device section and added the extra section to the end of the file.

I have a Dell Inspiron 1720 with an nVidia 8600M GT 256mb video card.  Below is a dump after entering 'compiz --replace -v'

Checking for Unsupported sessions: not present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 
Checking for FBConfig: present. 
Checking for texture_from_pixmap: present. 
Checking for copy texture support: present. 
Checking for Intel: not present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for XDamage extension: present. 
Checking for XSync extension: present. 
Detected 1 screen(s)
Checks indicate compiz should work on your system
Found GNOME desktop environment running...
Found running windows manager: metacity
Setting fallback windows manager to metacity 
Loading the ccp settings interface
Exporting: __GL_YIELD=NOTHING WINDOW_MANAGER=/usr/bin/compiz 
Executing: /usr/bin/compiz.real --ignore-desktop-hints --replace --sm-disable ccp 
Backend     : gconf
Integration : true
Profile     : default
Adding plugin mblur (mblur)
Adding plugin mousegestures (mousegestures)
Adding plugin rotate (rotate)
Adding plugin shift (shift)
Adding plugin scale (scale)
Adding plugin addhelper (addhelper)
Adding plugin group (group)
Adding plugin notification (notification)
Adding plugin snap (snap)
Adding plugin thumbnail (thumbnail)
Adding core settings (General Options)
Adding plugin colorfilter (colorfilter)
Adding plugin keybinding (keybinding)
Adding plugin plane (plane)
Adding plugin widget (widget)
Adding plugin animation (animation)
Adding plugin switcher (switcher)
Adding plugin winrules (winrules)
Adding plugin screenshot (screenshot)
Adding plugin regex (regex)
Adding plugin expo (expo)
Adding plugin wall (wall)
Adding plugin screensaver (screensaver)
Adding plugin neg (neg)
Adding plugin crashhandler (crashhandler)
Adding plugin imgjpeg (imgjpeg)
Adding plugin inotify (inotify)
Adding plugin resizeinfo (resizeinfo)
Adding plugin scaleaddon (scaleaddon)
Adding plugin annotate (annotate)
Adding plugin cubecaps (cubecaps)
Adding plugin put (put)
Adding plugin atlantis (atlantis)
Adding plugin place (place)
Adding plugin ezoom (ezoom)
Adding plugin ring (ring)
Adding plugin trailfocus (trailfocus)
Adding plugin wobbly (wobbly)
Adding plugin video (video)
Adding plugin showdesktop (showdesktop)
Adding plugin cube (cube)
Adding plugin water (water)
Adding plugin png (png)
Adding plugin kiosk (kiosk)
Adding plugin svg (svg)
Adding plugin fs (fs)
Adding plugin visualevent (visualevent)
Adding plugin opacify (opacify)
Adding plugin move (move)
Adding plugin quickchange (quickchange)
Adding plugin cheatsheet (cheatsheet)
Adding plugin vpswitch (vpswitch)
Adding plugin reflex (reflex)
Adding plugin extrawm (extrawm)
Adding plugin decoration (decoration)
Adding plugin flash (flash)
Adding plugin splash (splash)
Adding plugin fadedesktop (fadedesktop)
Adding plugin workarounds (workarounds)
Adding plugin firepaint (firepaint)
Adding plugin bench (bench)
Adding plugin gotovp (gotovp)
Adding plugin fade (fade)
Adding plugin resize (resize)
Adding plugin blur (blur)
Adding plugin zoom (zoom)
Adding plugin scalefilter (scalefilter)
Adding plugin dbus (dbus)
Adding plugin 3d (3d)
Adding plugin clone (clone)
Adding plugin cubereflex (cubereflex)
Adding plugin gears (gears)
Adding plugin glib (glib)
Adding plugin minimize (minimize)
Adding plugin wallpaper (wallpaper)
Adding plugin text (text)
Initializing core options...done
Initializing place options...done
Initializing move options...done
Initializing vpswitch options...done
Initializing decoration options...done
Initializing fadedesktop options...done
Initializing workarounds options...done
Initializing firepaint options...done
Initializing resize options...done
Initializing blur options...done
Initializing zoom options...done
Initializing 3d options...done
Initializing minimize options...done
Initializing wobbly options...done
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/friction. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
GConf backend: There is an unsupported value at path /apps/compiz/plugins/wobbly/screen0/options/spring_k. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
Initializing video options...done
Initializing fade options...done
Initializing cube options...done
Initializing rotate options...done
Initializing scale options...done
Initializing switcher options...done
Initializing cubereflex options...done
Executing: metacity 

What could I be doing wrong?

Thanks,
RMF

---

### Post by rmflagg on 2007-08-06
Oh yeah, there is this error that keeps showing up also

/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32
/usr/bin/compiz.real (core) - Warn: No GLXFBConfig for depth 32

RMF

---

### Post by JerMe on 2007-08-06
Try removing beryl-manager and anything left from the older beryl install.  Reboot, then issue **compiz --replace** and see what you get.  You can also try **compiz --replace -c emerald** if you have an updated version of emerald.

---

### Post by psyopper on 2007-08-06
Try setting your default color depth to 24 (not 32) in your xorg.conf. Actually, if you could post the contents of your /etc/X11/xorg.conf here that would be a great help in getting you an answer!

---

### Post by rmflagg on 2007-08-09
Ok,
   Here is my xorg.conf.  I noticed that the color depth is set to 24 bit.  I am pretty much stumped.

Thanks,
RMF

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
#    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
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

#Section "InputDevice"
#    Identifier     "Configured Mouse"
#    Driver         "mouse"
#    Option         "CorePointer"
#    Option         "Device" "/dev/input/mice"
#    Option         "Protocol" "ImPS/2"
#    Option         "ZAxisMapping" "4 5"
#    Option         "Emulate3Buttons" "true"
#EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig"	"on"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 40.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "backingstore" "True"
    Option         "TripleBuffer" "True"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "800x600"
    EndSubSection
EndSection

Section "Extensions"
	Option	"Composite" "Enable"
EndSection

---

### Post by llzero1337 on 2007-08-09
> **hyperair said:**
> You upgraded to Feisty eh? Perhaps you might have had your xorg.conf overwritten. Run this command:
```

sudo nvidia-xconfig --add-argb-glx-visuals

```
in the terminal and restart your X server.

Thanks this worked for me 4 :):lolflag:

---

### Post by psyopper on 2007-08-09
Actually your xorg.conf shows 

DefaultDepth 16

Try changing it to

DefaultDepth 24

and then restart X.

---

### Post by wiseberg on 2007-08-10
> **hyperair said:**
> 
```

sudo nvidia-xconfig --add-argb-glx-visuals

```


This one also works for me , am I No.5?:)

---

### Post by rmflagg on 2007-08-11
Ok, changing the default depth(which I must say that I completely missed) to 24bit did the trick!  I now have all the bells and whistles!
One thing that I have noticed: I have a new Dell Inspiron 1720 with 2Gb of ram and the nVidia 8600M GT 256Mb video card and some of the window effects(burn, etc.) still run *really* slow, some to the point of not being visible.  Is this still due to the Beta nature of Compiz-Fusion?

Thanks so much!,
RMF

---

### Post by hyperair on 2007-08-11
I hear that if you start Compiz with "--loose-binding" it'll run faster. It definitely does on my system. Takes up less CPU too.

```
compiz --replace --loose-binding -c emerald
```

---

### Post by jtreach on 2007-08-11
I also have the no window borders trouble, running **emerald --replace** and **compiz --replace -c emerald** works for me but how do I make this problem go away permanently? Affixing & to the end of the command does not seem to help as when I exit the terminal session the window borders promptly disappear. I have already uninstalled the beryl manager and beryl from a previous beryl installation.

---

### Post by autocrosser on 2007-08-11
You could create a script to start Compiz. I have a simple one I got from another thread--Open a text editor & copy/paste this:

#!/bin/sh

# click to start, click to stop

if pidof compiz.real
then
 exec metacity --replace
else
 exec compiz --replace --loose-binding -c emerald

fi



This one will toggle Compiz on/off--I even just included hyperair's loose-binding add--makes it much faster!! Call it something descriptive--mine is compiz_start.

I put it in my /home folder & then opened a terminal:

chmod 777 /home/dean/compiz_start

then make a launcher for your panel or menu---

add to panel>Custom Application Launcher

and you have a one-click way to start/stop Compiz.

---

### Post by dirn on 2007-08-12
Go to System -> Preferences -> Sessions, 
at **Startup Programs** tab, click **New** button and type **compiz --replace -c emerald &** to **Command** text box

---

### Post by jtreach on 2007-08-12
Compiz starts automatically for me, so won't using the above command on startup give me two instances of it? Or am I just being an idiot?

---

### Post by autocrosser on 2007-08-12
I removed the auto-start & just toggle with the script...I feel that I have more control over it that way.....

If you call it with a script you might have two running instances---would be a bad thing.....

---

### Post by iamjfarrell on 2007-08-12
I am having the no borders problem as well and that replace code does not work..

---

### Post by dirn on 2007-08-12
> **jtreach said:**
> Compiz starts automatically for me, so won't using the above command on startup give me two instances of it? Or am I just being an idiot?

If compiz start automatically, i guess **emerald --replace** command would be enough in the startup. Thank you for telling this, I'll try this tonight.

---

### Post by dirn on 2007-08-13
it seems like compiz-fusion is not automatically start on my machine. i guess i'll just stick to my previous command on startup :D

---

### Post by Frak on 2007-08-13
Are you sure your not using either Gutsy (which has Compiz-Fusion on startup by default) or you aren't using Desktop Effects in System->Preferences?

---

### Post by dirn on 2007-08-14
I'm using Feisty, didn't noticed that you guys were talking about Gutsy. Sorry :D

---

### Post by psyopper on 2007-08-14
> **jtreach said:**
> I also have the no window borders trouble, running **emerald --replace** and **compiz --replace -c emerald** works for me but how do I make this problem go away permanently? Affixing & to the end of the command does not seem to help as when I exit the terminal session the window borders promptly disappear. I have already uninstalled the beryl manager and beryl from a previous beryl installation.

If you launch something from the terminal, the terminal must stay open for it to run. Try this: Launch  gedit from the terminal
```
gedit
```

After gedit launches, close the terminal -- Gedit will also close. To get around this try launching from the run line by pressing [Alt]+[F2].

For those with startup scripts and the like, try using Fusion Icon. It's available in the various repositories (Trevino or Vorian) as fusion-icon.
```
sudo aptitude install fusion-icon
```

Fusion Icon is very similar to the Beryl Icon of yore giving you shortcuts to the CCSM, Emerald Theme Manager, settings and selections of which window decorator and manager you would like to use in a convenient icon that sits in your Notification Area.

---

### Post by rozhman on 2007-08-15
Run** ccsm** from terminal .Enable "Windows Decoration".Then press alt+F2 .
type metacity --replace .
Press alt+F2 again  and type compiz --replace -c emerald & .

---

### Post by lavs23 on 2007-08-15
I'm still not getting any borders and I haven't been able to figure it out.  I've attached my xorg.conf does anybody have any ideas?  I've gotten Compiz Fusion to work before but I'm not having any luck right now.

```


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
    Load           "extmod"
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 72.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G70 [GeForce Go 7600]"
    Driver         "nvidia"
    Option	"RenderAccel" "true"
    Option	"AllowGLXWithComposite" "true"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G70 [GeForce Go 7600]"
    Monitor        "Generic Monitor"
    DefaultDepth   24
    Option	"AddARGBGLXVisuals" "true"
    Option         "DisableGLXRootClipping" "true"
    Option         "NoLogo" "true"
    SubSection     "Display"
        Depth       24
        Modes      "1440x900"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

Any help would be much appreciated.

---

### Post by 99vadim on 2007-08-16
> **rozhman said:**
> Run** ccsm** from terminal .Enable "Windows Decoration".Then press alt+F2 .
type metacity --replace .
Press alt+F2 again  and type compiz --replace -c emerald & .

Thanks, the method works just fine for me.

---

### Post by sakul07 on 2007-08-16
I updated my nvidia drivers... and Beryl, Emerald and Compiz start malfunctioning... beryl and compiz fusion work.... but without borders.... and emerald is like dead... my borders doesn't get emerald themes... i think it's related with my xorg.conf file... any idea??

my xorg:

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:40:26 PDT 2007
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
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
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
    Load           "vbe"
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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7600"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    Option         "AddARGBGLXVisuals" "True"
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

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    16
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900 +0+0; 800x600 +0+0; 640x480 +0+0"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "Coolbits" "1"
    Option         "TripleBuffer" "true" # + Rapido pero + RAM
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       16
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

---

### Post by hyperair on 2007-08-16
In the SubSection "Display" change your Depth to 24.

---

### Post by sakul07 on 2007-08-16
Now a NVIDIA sign appears before the logon username square! but Emmerald, beryl and Compiz Fusion still not working.....

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:39:30 PDT 2007

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Jun 13 18:40:26 PDT 2007
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
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
    InputDevice    "Synaptics Touchpad"
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
    Load           "dri"
    Load           "vbe"
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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     60.0
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"
    Option         "RenderAccel" "true"
    Option 	   "AllowGLXWithComposite" "true"
    Option	   "Coolbits" "1"
    Option         "TripleBuffer" "true" # + Rapido pero + RAM
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7600"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    Option         "AddARGBGLXVisuals" "True"
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

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1440x900 +0+0; 800x600 +0+0; 640x480 +0+0"
    Option         "RenderAccel" "true"
    Option         "AllowGLXWithComposite" "true"
    Option         "Coolbits" "1"
    Option         "TripleBuffer" "true" # + Rapido pero + RAM
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by Frak on 2007-08-16
There's not supposed to be an NVidia logo there?

---

### Post by ionman on 2007-08-16
Following along the same lines...

Here is what I have:

A fresh install of Feisty
I followed this guide: [http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)
I used Envy to install the video driver


Here is what my xorg.conf looks like:

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
    InputDevice    "Synaptics Touchpad"
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
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"		# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G72M [GeForce Go 7400]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [GeForce Go 7400]"
    Monitor        "Generic Monitor"
    DefaultDepth    16
    SubSection     "Display"
        Depth       1
        Modes      "1920x1200" "1680x1050" "1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1920x1200" "1680x1050" "1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1920x1200" "1680x1050" "1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1920x1200" "1680x1050" "1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1920x1200" "1680x1050" "1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1920x1200" "1680x1050" "1600x1200" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

Here is the problem: I can run Compiz Fusion in 16bit color mode. 24bit does not run at all, and if I try 32 my X server does not start. Even when I run in 16bit, I don't have any window borders. I have emerald and emerald-themes installed, and the -c emerald paramater for compiz doesn't work either. (BTW, I when I changed to 24bit color mode, I got the NVIDIA splash screen as well.)

I think I have a very similar problem as others, but I am just not finding a solution. I tried extensive searching, but was unable to come up with anything, so sorry if this is redundant. I am lost. Any help here would be most appreciated. Thanks!

- ionman

---

### Post by ionman on 2007-08-16
Actually I have fixed it. I don't know exactly what the problem was, though. I didn't have anything installed yet so I just re-installed ubuntu. I followed the tutorial much more carefully this time, and I also made sure that I installed all of the updates before installing anything else. I think this, combined with the fact that I perfected my xorg.conf (finally using 32bit color depth) before I installed compiz. Everything is working great now. Thanks to all you out there writing helpful stuff for us users muddling through this!

- ionman

---

### Post by Luffield on 2007-08-17
> **hyperair said:**
> You upgraded to Feisty eh? Perhaps you might have had your xorg.conf overwritten. Run this command:
```

sudo nvidia-xconfig --add-argb-glx-visuals

```
in the terminal and restart your X server.
Thanks, it worked for me too.
I'm using gutsy and I got a new screen, had to start nvidia-settings to get the new resolution activated and it must have overwritten something on my xorg.conf.

---

### Post by Duranxl on 2007-08-19
the "sudo nvidia-xconfig --add-argb-glx-visuals" doesn't work for me.. 
it says the file is overwritten, i restart with ctrl+alt+backspace.. and after 2secs the problem is back again.blank terminal and no bars..
any help:(?

HM i think adding -d 24 worked..
:]

---

### Post by icic on 2007-09-19
Thank you so much!  changing the default depth from 16 to 24 has fixed everything!!!!

---

### Post by hyperair on 2007-09-20
No problem =)

---

