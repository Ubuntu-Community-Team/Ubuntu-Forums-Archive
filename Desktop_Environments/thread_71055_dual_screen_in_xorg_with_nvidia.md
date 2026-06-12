---
title: "dual screen in xorg with nvidia"
date: 2005-10-02
forum: Desktop Environments
---

### Post by strips on 2005-10-02
Hi. I've been at it for a while to get a dual screen in Xorg with a Nvidia 4200 Go card. I'm using this now on an Inspiron 8600.

So finally I got it working. In this method X controls the screens. Since you have to declare to separate screens in the X config.

Sorry about the formatting of this post. There is obviusly a bug in the forum so I'm not able to format the code properly. Tabs and enters disappear where they shouldn't. 

```

Section "Device"
#Laptop screen
Identifier      "NV28_0"
Driver          "nvidia"
BusID           "PCI:1:0:0"
Option          "RenderAccel"           "true"
Option          "AllowGLXWithComposite" "true"
Option          "UseEdidFreqs"          "true"
Option		"ConnectedMonitor"	"DFP-0"
Screen		0
EndSection
```

```

Section "Device"
#External screen
Identifier	"NV28_1"
Driver		"nvidia"
BusID		"PCI:1:0:0"
Option		"RenderAccel" 		"true"
Option		"AllowGLXWithComposite" "true"
Option 		"UseEdidFreqs" 		"true"
Option          "ConnectedMonitor"      "CRT-0"
Screen 		1
EndSection
```

Observe that as soon as dual diplay or TwinView is started, the external connector on a Nvidia laptop is considered the PRIMARY display. If you don't have a laptop you just have to figure out what's your primary output.

Another thing is "UseEdidFreqs" in the Device section. As long as your monitor returns its freqs you don't need Horiz and Vert refresh rates in the Monitor sections. Comment out HorizSync and VertRefresh and se if it works. If it does, they're not necessary.

```

Section "Monitor"
#Laptop monitor
Identifier	"Monitor_0"
Option		"DPMS"
#HorizSync	28-84
#VertRefresh	43-60
DisplaySize 	331 207
EndSection
```

The DiplaySize is your monitor size in millimeters. Editing theese changes the DPI within the driver. I recommend to comment this line if you don't have too large or small fonts in X.

```

Section "Monitor"
#External monitor
Identifier      "Monitor_1"
Option          "DPMS"
#HorizSync      28-84
#VertRefresh    43-60
EndSection
```

```

Section "Screen"
#Laptop screen
Identifier	"Screen_0"
Device		"NV28_0"
Monitor		"Monitor_0"
DefaultDepth	24
SubSection "Display"
Depth		24
Modes		"1680x1050"
EndSubSection
EndSection
```

```

Section "Screen"
#External screen
Identifier      "Screen_1"
Device          "NV28_1"
Monitor         "Monitor_1"
DefaultDepth    24
SubSection "Display"
Depth           24
Modes           "1024x768"
EndSubSection
EndSection
```

After doing this dual setup I realize that the Modes option is totally ignored by X. It obviously uses the EdidFreqs and gived you the max/best resolution. I'm not able to change the resolution in this file. This is new to me. But.... Now I can change the resolution on the fly in Gnome. System -> Brukervalg/User options -> Skjermoppl&#248;sning/Screen resolution. (Sorry if the English translation is wrong).

```

Section "ServerLayout"
Identifier	"Default Layout"
Screen		0 "Screen_0" #Laptop screen
Screen          1 "Screen_1" RightOf "Screen_0" #External screen
InputDevice	"Generic Keyboard"
InputDevice	"Configured Mouse"
InputDevice	"Alps Touchpad"
InputDevice	"BTMouse"
InputDevice     "Mice"
Option 		"AllowMouseOpenFail" "1"
EndSection
```

The RightOf statement above only adjusts where to move the mouse to switch screen.

I have done alot og trial and failure with this setup. Remember that this is the way to do it if you want X to be aware of more than one display. An alternative is to use Nvidias TwinView options. Both these solutions is mentioned in Nvidias readme file.

Everything I have done here is from reading the Nvidia README (comes with the driver and available on web from Nvidia) and "man xorg.conf".

Good luck ;)

Regards 
Stian H. Larssen

---

