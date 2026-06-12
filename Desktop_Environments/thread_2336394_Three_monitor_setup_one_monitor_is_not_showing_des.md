---
title: "Three monitor setup one monitor is not showing desktop"
date: 2016-09-07
forum: Desktop Environments
---

### Post by zedmor on 2016-09-07
Tried to setup three monitors, drivers and everything woks fine, desktop even appears there on login screen but when I login to my user account 3rd monitor stays black (I can see mouse pointer on it but can't move any windows or see background).

Here's my config:

~/.config/monitors.xml

```
<monitors version="1">  <configuration>
      <clone>no</clone>
      <output name="DVI-I-0">
          <vendor>HWP</vendor>
          <product>0x2690</product>
          <serial>0x01010101</serial>
          <width>2560</width>
          <height>1600</height>
          <rate>60</rate>
          <x>0</x>
          <y>1080</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>yes</primary>
      </output>
      <output name="HDMI-0">
      </output>
      <output name="DP-0">
      </output>
      <output name="DP-1">
      </output>
      <output name="DVI-D-0">
          <vendor>DEL</vendor>
          <product>0x4035</product>
          <serial>0x3433374c</serial>
          <width>2560</width>
          <height>1600</height>
          <rate>60</rate>
          <x>2590</x>
          <y>1080</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="VGA-1">
      </output>
      <output name="HDMI-1">
          <vendor>ACR</vendor>
          <product>0x02ca</product>
          <serial>0x21109a35</serial>
          <width>1920</width>
          <height>1080</height>
          <rate>60</rate>
          <x>1543</x>
          <y>0</y>
          <rotation>normal</rotation>
          <reflect_x>no</reflect_x>
          <reflect_y>no</reflect_y>
          <primary>no</primary>
      </output>
      <output name="DP-1">
      </output>
      <output name="HDMI-2">
      </output>
      <output name="HDMI-3">
      </output>
  </configuration>
</monitors>
```

/home/<user>/xorg.conf.new
```
Section "ServerLayout"	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection


Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "built-ins"
EndSection


Section "Module"
	Load  "glx"
EndSection


Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection


Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection


Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
EndSection


Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"           	# [<bool>]
        #Option     "HWcursor"           	# [<bool>]
        #Option     "NoAccel"            	# [<bool>]
        #Option     "ShadowFB"           	# [<bool>]
        #Option     "VideoKey"           	# <i>
        #Option     "WrappedFB"          	# [<bool>]
        #Option     "GLXVBlank"          	# [<bool>]
        #Option     "ZaphodHeads"        	# <str>
        #Option     "PageFlip"           	# [<bool>]
        #Option     "SwapLimit"          	# <i>
        #Option     "AsyncUTSDFS"        	# [<bool>]
        #Option     "AccelMethod"        	# <str>
        #Option     "DRI"                	# <i>
	Identifier  "Card0"
	Driver      "nouveau"
	BusID       "PCI:1:0:0"
EndSection


Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection



```


what I can do there? where whole desktop configurated? Is it even possitble to have setup like this: two monitors at bottom side by side and third up top in the middle of those

---

### Post by QIII on 2016-09-07
Hello!

It would be helpful for us to know:

1.  What flavor and release of Ubuntu you are using.
2.  The manufacturer and model of your GPU.
3.  What driver you have installed.

Cheers!

---

### Post by zedmor on 2016-09-07
16.04 desktop, gpus are nvidia gtx 970 and intel onboard graphics with native drivers. I do not think problem with drivers - I can move mouse pointer to 3rd montor and if I select it as only display it shows desktopjust fine, but now with two others....
May be someone knows where in X server config you can say how big your desktop is and where put wallpaper/windows.

---

