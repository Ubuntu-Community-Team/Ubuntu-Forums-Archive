---
title: "Can't run Desktop effects on computer running Nvidia graphics card"
date: 2007-11-20
forum: Desktop Effects &amp; Customization
---

### Post by greatnugget on 2007-11-20
Hello all,

Noob here. Still trying to figure out Ubuntu. I just installed Gutsy Gibbon on my computer and am trying to get it to run the desktop effects, but I'm having a bit of trouble.

When I first tried to enable the desktop effects in System>Preferences>Appearance[Visual Effects] it told me that it was unable because my graphics driver was not installed (I am running an Nvidia graphics driver; unsure of model; Dell i8600 purchased in April of 2004). I updated my driver so that my Restricted Drivers Manager shows that my "Nvidia accelerated graphics driver (latest cards)" is "in use". However, when I try to enable the Visual Effects I get "Desktop effects could not be enabled" (this is when I try either "normal" or "extra"). 

Could someone tell me what I am doing wrong?

I am familiar with the Terminal, but not this "Compiz" I keep seeing on the forum.

Thanks ahead of time,
G-Nugget

---

### Post by overdrank on 2007-11-20
> **greatnugget said:**
> Hello all,

Noob here. Still trying to figure out Ubuntu. I just installed Gutsy Gibbon on my computer and am trying to get it to run the desktop effects, but I'm having a bit of trouble.

When I first tried to enable the desktop effects in System>Preferences>Appearance[Visual Effects] it told me that it was unable because my graphics driver was not installed (I am running an Nvidia graphics driver; unsure of model; Dell i8600 purchased in April of 2004). I updated my driver so that my Restricted Drivers Manager shows that my "Nvidia accelerated graphics driver (latest cards)" is "in use". However, when I try to enable the Visual Effects I get "Desktop effects could not be enabled" (this is when I try either "normal" or "extra"). 

Could someone tell me what I am doing wrong?

I am familiar with the Terminal, but not this "Compiz" I keep seeing on the forum.

Thanks ahead of time,
G-Nugget
Hi and welcome if you could find your exact model with the command in the terminal ```
lspci
``` Then you may need to add these to your xorg under the device section.
Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
Under the section device. To edit your xorg use this command 
```
gksudo gedit /etc/X11/xorg.conf
```
And you may have to use this command also
 ```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24

```
Hope this helps. Good luck!

---

### Post by greatnugget on 2007-11-20
Here's my graphics driver model: GeForce FX Go5200 64M

I tried that other stuff but it didn't seem to work. I only tried the Terminal commands. I don't follow the other things.:(

---

### Post by overdrank on 2007-11-20
> **greatnugget said:**
> Here's my graphics driver model: GeForce FX Go5200 64M

I tried that other stuff but it didn't seem to work. I only tried the Terminal commands. I don't follow the other things.:(

HI and here is a link if you would like to investigate
[http://xorg.freedesktop.org/wiki/](http://xorg.freedesktop.org/wiki/)
And I failed to mention in the first post that it is wise to backup your xorg before making changes in the event that the xorg crashes.
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Basically you sometimes have to tweak the file to achieve the result you are looking for. For example here is a copy of mine, you can see the mention lines highlighted. 
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
    Identifier     "WDE LCM-19v1"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
[COLOR="Red"]Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"[/COLOR]
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV43 [GeForce 6600 GT]"
    Monitor        "WDE LCM-19v1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection
```
I hope this helps in a little of the clarifications. Good luck!

---

### Post by ZaphodNE on 2007-11-20
I had Nvdia woes as well with a newer model (I think) than yours, but maybe this will help.....search for a thread in the same catagory you're in now for either my user ID ( ZaphodNE )  or this subject line    "compiz with nvidia geforce 6150 le a total wreck on gusty"

Hope this turns out to be of help.  Seems other folks are steering you in this direction as well.  Luck, dude!

---

### Post by greatnugget on 2007-11-21
Ok, thanks everyone for the advice. I appreciate it, but I'm still having problems.

> **overdrank said:**
> To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
``` 


I tried to do this in my Terminal but it told me: 

cp; cannot stat `/etc/Xll/xorg.conf': No such file or directory

Am I somehow missing my xorg.conf file? If so, what can I do to get a new one?

Thanks again

---

### Post by greatnugget on 2007-11-21
ok a little embarrassed here. I just realized I was putting 'l's' where I needed to be putting '1's'. :oops: :oops: :oops:

However I'm still having problems. This is the message I'm getting now:

cp: target `/etc/X11/xorg.conf-backup' is not a directory

Again, any help is greatly appreciated.

---

### Post by greatnugget on 2007-11-21
Ok, figured a few more things out, but still having problems.

Figured out how to edit my xorg.conf file. Added these lines under 'Device'

	Option	"AddARGBVisuals"	"True"
	Option	"AddARGBLXVISUALS"	"True"
	Option	"NoLogo"	"True"

However when I try to enable my Visual Effects it still won't do it.

---

