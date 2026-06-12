---
title: "no hardware acceleration"
date: 2006-10-15
forum: Desktop Environments
---

### Post by {spitFire} on 2006-10-15
Hi,
  I'm using Ubuntu Dapper on my Dell-Inspiron E1505. There is no hardware acceleration on my system. The system has a Ati Mobility Radeon X1300 card. 
  When I run fglrxinfo in the command line, this is what I get
  
  ----------------------------------
  display: :0.0  screen: 0
  OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
  OpenGL renderer string: Mesa GLX Indirect
  OpenGL version string: 1.2 (1.5 Mesa 6.4.1)
  ----------------------------------

  And I also note that there are several weird things in my xorg.conf file, the contents of which are as follows:

  ----------------------------------
[INDENT] Section "ServerLayout"
         Identifier     "Default Layout"
         Screen      0  "aticonfig-Screen[0]" 0 0
         InputDevice    "Generic Keyboard"
         InputDevice    "Configured Mouse"
         InputDevice    "stylus" "SendCoreEvents"
         InputDevice    "cursor" "SendCoreEvents"
         InputDevice    "eraser" "SendCoreEvents"
         InputDevice    "Synaptics Touchpad"
 EndSection
 
 Section "Files" 

         # path to defoma fonts
         FontPath     "/usr/share/X11/fonts/misc"
         FontPath     "/usr/share/X11/fonts/cyrillic"
         FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
         FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
         FontPath     "/usr/share/X11/fonts/Type1"
         FontPath     "/usr/share/X11/fonts/100dpi"
         FontPath     "/usr/share/X11/fonts/75dpi"
         FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
 EndSection

 Section "Module"
         Load  "i2c"
         Load  "bitmap"
         Load  "ddc"
         Load  "dri"
         Load  "extmod"
         Load  "freetype"
         Load  "glx"
         Load  "int10"
         Load  "type1"
         Load  "vbe"
 EndSection 

 Section "InputDevice"
         Identifier  "Generic Keyboard"
         Driver      "kbd"
         Option      "CoreKeyboard"
         Option      "XkbRules" "xorg"
         Option      "XkbModel" "pc104"
         Option      "XkbLayout" "us"
 EndSection

 Section "InputDevice"
         Identifier  "Configured Mouse"
         Driver      "mouse"
         Option      "CorePointer"
         Option      "Device" "/dev/input/mice"
         Option      "Protocol" "ExplorerPS/2"
         Option      "ZAxisMapping" "4 5"
         Option      "Emulate3Buttons" "true"
 EndSection

 Section "InputDevice"
         Identifier  "Synaptics Touchpad"
         Driver      "synaptics"
         Option      "SendCoreEvents" "true"
         Option      "Device" "/dev/psaux"
         Option      "Protocol" "auto-dev"
         Option      "HorizScrollDelta" "0"
 EndSection

 Section "InputDevice" 

                                                       # /dev/input/event
                                                       # for USB
         Identifier  "stylus"
         Driver      "wacom"
         Option      "Device" "/dev/wacom"          # Change to
         Option      "Type" "stylus"
         Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
 EndSection

 Section "InputDevice"
 
                                                       # /dev/input/event
                                                       # for USB
         Identifier  "eraser"
         Driver      "wacom"
         Option      "Device" "/dev/wacom"          # Change to
         Option      "Type" "eraser"
         Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
 EndSection

 Section "InputDevice"

                                                       # /dev/input/event
                                                       # for USB
         Identifier  "cursor"
         Driver      "wacom"
         Option      "Device" "/dev/wacom"          # Change to
         Option      "Type" "cursor"
         Option      "ForceDevice" "ISDV4"               # Tablet PC ONLY
 EndSection

 Section "Monitor"
         Identifier   "Generic Monitor"
         Option      "DPMS"
 EndSection

 Section "Monitor"
         Identifier   "aticonfig-Monitor[0]"
         Option      "VendorName" "ATI Proprietary Driver"
         Option      "ModelName" "Generic Autodetecting Monitor"
         Option      "DPMS" "true"
 EndSection

 Section "Device"
         Identifier  "ATI Technologies, Inc. ATI Default Card"
         Driver      "fglrx"
         BusID       "PCI:1:0:0"
 EndSection

 Section "Device"
         Identifier  "aticonfig-Device[0]"
         Driver      "fglrx"
         Option      "VideoOverlay" "on"
         Option      "OpenGLOverlay" "off"
 EndSection

 Section "Screen"
          Identifier "Default Screen"
          Device     "ATI Technologies, Inc. ATI Default Card"
          Monitor    "Generic Monitor" 
         DefaultDepth     24
         SubSection "Display"
                 Depth     1
                 Modes    "1200x800" "1024x768"
         EndSubSection
         SubSection "Display"
                 Depth     4
                 Modes    "1200x800" "1024x768"
         EndSubSection
         SubSection "Display"
                 Depth     8
                 Modes    "1200x800" "1024x768"
         EndSubSection
         SubSection "Display"
                 Depth     15
                 Modes    "1200x800" "1024x768"
         EndSubSection
         SubSection "Display"
                 Depth     16
                 Modes    "1200x800" "1024x768"
         EndSubSection
         SubSection "Display"
                 Depth     24
                 Modes    "1200x800" "1024x768"
         EndSubSection
 EndSection

 Section "Screen"
         Identifier "aticonfig-Screen[0]"
         Device     "aticonfig-Device[0]"
         Monitor    "aticonfig-Monitor[0]"
         DefaultDepth     24
         SubSection "Display"
                 Viewport   0 0
                 Depth     24
         EndSubSection
 EndSection

 Section "DRI"
         Mode         0666
 EndSection[/INDENT]
  ----------------------------------

  Can someone tell me how to resolve this problem?

---

### Post by jocko on 2006-10-15
What output do you get if you run this in a terminal?

```
cat /var/log/Xorg.0.log | grep EE
```

---

### Post by cookfromfrozen on 2006-10-15
Please don't take this as an insult to your intelligence because it isn't, but you don't mention that you've installed the ATI drivers...have you?

If not, [here is](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29) a good guide.

---

### Post by jocko on 2006-10-15
> **cookfromfrozen said:**
> Please don't take this as an insult to your intelligence because it isn't, but you don't mention that you've installed the ATI drivers...have you?

If not, [here is]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_1:_Installing_Dapper.27s_Included_Driver_.288.25.18.29") a good guide.

He must have them installed already, otherwise he would not be able to run fglrxinfo, which gets installed as a part of ati's drivers. I'm sure Xorg.0.log will say why it doesn't work.

---

### Post by cookfromfrozen on 2006-10-15
Oh okay, I must have been confusing it with glxinfo, that's installed even if you don't have the ATI drivers, right?

I hope that log file has the answer for him.

---

### Post by {spitFire} on 2006-10-15
$cat /var/log/Xorg.0.log | grep EE
Current Operating System: Linux phoenix 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

---

### Post by {spitFire} on 2006-10-15
Hi,
  I have installed the proprietory ati drivers and in fact, just a week back had xgl & compiz running smoothly. However, because of certain partition problems I had to re-install the system and after that I'm facing this problem.
  And, all sorts of questions are welcome. I just want to make sure I can run Beryl on my system (which IMHO is not possible without hardware acceleration). 
  I've included the message in the Xorg log and it reports of an incompatible kernel module. Now, how do I fix this?
  Kindly, help me resolve the problems.

---

### Post by jocko on 2006-10-16
> **{spitFire} said:**
> $cat /var/log/Xorg.0.log | grep EE
...
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
...


Did you install the drivers from ati.com? In that case you need to make sure you don't use the module from linux-restricted-modules. Try this:
```
sudo gedit /etc/default/linux-restricted-modules-common
```Make it look like this:```
DISABLED_MODULES="fglrx"
```Keep your fingers crossed and reboot. Let us know if it works or if you get any new error.

---

### Post by {spitFire} on 2006-10-16
> **jocko said:**
> Did you install the drivers from ati.com? In that case you need to make sure you don't use the module from linux-restricted-modules. Try this:
```
sudo gedit /etc/default/linux-restricted-modules-common
```Make it look like this:```
DISABLED_MODULES="fglrx"
```Keep your fingers crossed and reboot. Let us know if it works or if you get any new error.

Now, this is what I have in Xorg - log. 

Current Operating System: Linux phoenix 2.6.15-27-686 #1 SMP PREEMPT Sat Sep 16 02:13:27 UTC 2006 i686
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER
(EE) fglrx(0): DRIScreenInit failed!
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

---

### Post by jocko on 2006-10-16
> **{spitFire} said:**
> Now, this is what I have in Xorg - log. 

(EE) fglrx(0): DRIScreenInit failed!

I don't know what's causing that error. I saw you have several monitor, device and screen sections in your xorg.conf. Try starting with a fresh xorg.conf. (run 'sudo dpkg-reconfigure xserver-xorg')

---

### Post by {spitFire} on 2006-10-20
> **jocko said:**
> I saw you have several monitor, device and screen sections in your xorg.conf. Try starting with a fresh xorg.conf. (run 'sudo dpkg-reconfigure xserver-xorg')
First of all, I don't have several monitors, and I don't know how I ended up getting several in this configuration file. Secondly, what do the screens indicate?

---

