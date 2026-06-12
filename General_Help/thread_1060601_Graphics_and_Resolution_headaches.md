---
title: "Graphics and Resolution headaches"
date: 2009-02-04
forum: General Help
---

### Post by drewbacca on 2009-02-04
Hello, I recently talked my friend into switching to Ubuntu because of how easy it is to use. However, I am finding that I may have been a liar.

I am running Ubuntu 8.10 for him.

My friend has a GeForce 8600 GT graphics card and a 22 inch widescreen monitor from Chi Mei. After fighting with xorg for 2 days I managed to get things almost working... except he couldn't have a display setting higher than 800 x 600. I know that he can have much higher than that.

I finally decided to just star over from scratch. I reinstalled the drivers for his graphics card, and wrote the xorg.conf file by hand. sudo dpkg-reconfigure xserver-xorg would not give me options to manually set the display settings. It only ever asked me about the keyboard layout and then exited wiping out my configuration and so when I rebooted it was always back into "low graphics mode."

Sadly, after starting over and getting the new drivers I have to start in low graphics mode anyway now. Yay! At start up NVidia complains and fails, and I get something about the screen being found, but not usuable.

This is my xorg config.

```

#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "keyboard"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
   #  CHIMEI CMV 221D monitor, 22in
    Identifier     "DELL 2007WFP"
    HorizSync       31.0 - 81.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "DELL 2007WFP"
    DefaultDepth    24
    Option         "RenderAccel" "True"
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

---

### Post by gettinoriginal on 2009-02-05
Have you checked your friends machine to make sure that the < System, Admin, Software Sources > is set right, the first 4 boxes should be checked, under third party all boxes except CD should be checked, and updates should have "Normal Releases".

---

### Post by drewbacca on 2009-03-24
Sorry for taking so long to get back to you, I only get so much time to see my friend or work on his computer. I have checked the sources and all match what you said and I still can not resolve the issue. What should I do?

This is my friends current xorg.conf:

```

Section "Screen"
	Identifier "Default Screen"
	Device "Default Device"
	Monitor "CHIMEI CMV 221D"
	DefaultDepth 24
	Option "RenderAccel" "True"
	Option "AllowGLXWithComposite" "True"
	Option "AddARGBGLXVisuals" "True"
	SubSection "Display"
		Depth 1
		Modes "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 4
		Modes "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 8
		Modes "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 15
		Modes "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 16
		Modes "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth 24
		Modes "1680x1050" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Monitor"
	Identifier "CHIMEI CMV 221D"
	HorizSync 30.0 - 82.0
	VertRefresh 56.0 - 76.0
	Option "DPMS"
EndSection

Section "Module"
	Load	"glx"
EndSection

Section "Device"
	Identifier	"Default Device"
	Driver	"nvidia"
	Option	"NoLogo"	"True"
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

```

---

