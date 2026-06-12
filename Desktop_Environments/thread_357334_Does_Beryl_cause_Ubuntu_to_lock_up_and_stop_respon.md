---
title: "Does Beryl cause Ubuntu to lock up and stop responding?"
date: 2007-02-09
forum: Desktop Environments
---

### Post by presbp on 2007-02-09
I have Beryl installed and have it as the window manager.  Often Windows will just freeze and I cannot do anything.  I just have to shut the PC down and reboot to get it going again.

---

### Post by happy-and-lost on 2007-02-09
Beryl is beta software. Is your graphics card sufficiently configured?

---

### Post by AusIV4 on 2007-02-09
> **presbp said:**
> I have Beryl installed and have it as the window manager.  Often Windows will just freeze and I cannot do anything.  I just have to shut the PC down and reboot to get it going again.
I can guarantee Beryl is not freezing Windows.

If by Windows you mean Linux, I'd suggest looking in Beryl Settings manager and disable things like blur, and water.

Also, what version of beryl are you running? I had some issues with Beryl a while back, but the latest version seems very stable.

---

### Post by presbp on 2007-02-09
the newest version, I have 2 gigs of DDR2 800Mhz RAM, Core 2 Duo E6600, nVidia 7800GT 256MB PCIeX16

---

### Post by 23meg on 2007-02-09
It may help if you post the contents of your /etc/X11/xorg.conf file.

---

### Post by GSF1200S on 2007-04-27
> **23meg said:**
> It may help if you post the contents of your /etc/X11/xorg.conf file.

**Edit** Whoops, didnt post it all.. look below for my xorg.conf

I dont know what happened, but Beryl is definitely causing the DE to freeze. I have to force shutdown with the power switch... Weird thing is, Ive never had a problem with Beryl before. Today, with no updates or anything, my Xwindow failed to load, and I had to reinstall my Nvidia drivers. The only thing Ive done that I can think of is install Diablo 2 under WINE. I know im ressurecting this post from the dead, but im a little lost.. Ubuntu runs forever on Metacity,,

---

### Post by GSF1200S on 2007-04-27
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
    Load           "dbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
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
    HorizSync       28.0 - 84.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AllowGLXWithComposite" "True"
    Option         "RenderAccel" "True"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by KrazyPenguin on 2007-04-27
This worked for me so far, I am currently trying to crash Beryl for the last hour lol

Edit your /boot/grub/menu.lst file.
Add noapic nolapic to the end of the 2.6.20-15 kernel line.

See:
[http://doc.gwos.org/index.php/Double_Clock_Speed](http://doc.gwos.org/index.php/Double_Clock_Speed)

and go half way down to the UBUNTU 32BIT SECTION.

If what I just said doesnt' work keep trying all the options one at a time.

I also included pci=assign-busses to the kernel.  
I had an error in /var/log/messages

It got rid of that error anyway.

Good luck!!!

---

