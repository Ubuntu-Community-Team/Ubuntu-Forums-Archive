---
title: "Screen resolution post ati fglrx drivers"
date: 2005-05-01
forum: Desktop Environments
---

### Post by AvvY on 2005-05-01
I have an ATI 9800 graphix card, so I installed the ato fglrx drivers so I could play games, but now I cannot change my screen resolution. I have tried to edit the xorg.conf file to fix it, but no luck. When I go System>Prefferences>Screen Resolution, I get an error "The X server doesn't support XRandR..."

Is there anyway to fix this so I can change the screen resolution. Currently it is about one or two settings higher than I'd like. I want it at 1024x768. If I cannot change it, what is the procedure to remove these new drivers, and go back to the default ATI drivers? My attempts at changing the xorg.conf file to remove this has ended in display problems.

Late,

---

### Post by AvvY on 2005-05-02
I have tried manually editing the xorg.conf file myself, but it causes problems of not being able to view anything when I boot and I have to restore it from backup. I have tried removing the fglrx driver code I manually inputted when installing them re: instructions, but that caused problems. I also tried removing the entries of higher resolutions to what I want, but also caused problems. Here is a readout of my xorg.conf file.

> Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
	Option "UseInternalAGPGART" "no"
	EndSection

Section "Monitor"
	Identifier	"L1710S"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
	Monitor		"L1710S"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "720x400" "640x480"
	EndSubSection
EndSection 

Late,

---

### Post by iomicifikko on 2005-05-02
i had the same problem, and trying to set good performance with my 9700mobility i was able to solve it but i dunno exactly what i did.

giving a look at my xorg i can tell u:

u set useinternalagpgart to "no" so be sure to load the agpgart kernel module (in /etc/modules add  "agpgart" at the end)


here is my module section in xorg.conf:

Section "Module"
        Load "GLcore"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
# Load "extmod" but omit DGA extension
# (the DGA extension is broken in the fglrx driver)
  SubSection "extmod"
    Option "omit xfree86-dga"
  EndSubSection

	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"record"
	Load	"type1"
	Load	"vbe"
EndSection



and if u need it here is my device section:

Section "Device"
    Identifier                          "ATI Technologies, Inc. Radeon Mobility 9600/9700 M10/M11 (RV350 NP)"
    Driver                              "fglrx"
# ### generic DRI settings ###
# === disable PnP Monitor  ===
    #Option                              "NoDDC"
# === disable/enable XAA/DRI ===
    Option "no_accel"                   "no"
    Option "no_dri"                     "no"
# === misc DRI settings ===
    Option "mtrr"                       "off" # disable DRI mtrr mapper, driver has its own code for mtrr
# ### FireGL DDX driver module specific settings ###
# === Screen Management ===
    Option "DesktopSetup"               "0x00000000" 
    Option "MonitorLayout"              "AUTO, AUTO"
    Option "IgnoreEDID"                 "off"
    Option "HSync2"                     "unspecified" 
    Option "VRefresh2"                  "unspecified" 
    Option "ScreenOverlap"              "0" 
# === TV-out Management ===
    Option "NoTV"                       "yes"     
    Option "TVStandard"                 "NTSC-M"     
    Option "TVHSizeAdj"                 "0"     
    Option "TVVSizeAdj"                 "0"     
    Option "TVHPosAdj"                  "0"     
    Option "TVVPosAdj"                  "0"     
    Option "TVHStartAdj"                "0"     
    Option "TVColorAdj"                 "0"     
    Option "GammaCorrectionI"           "0x06419064"
    Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
    Option "Capabilities"               "0x00000000"
# === Video Overlay for the Xv extension ===
    Option "VideoOverlay"               "on"
# === OpenGL Overlay ===
# Note: When OpenGL Overlay is enabled, Video Overlay
#       will be disabled automatically
    Option "OpenGLOverlay"              "off"
# === Center Mode (Laptops only) ===
    Option "CenterMode"                 "off"
# === Pseudo Color Visuals (8-bit visuals) ===
    Option "PseudoColorVisuals"         "off"
# === QBS Management ===
    Option "Stereo"                     "off"
    Option "StereoSyncEnable"           "1"
# === FSAA Management ===
    Option "FSAAEnable"                 "no"
    Option "FSAAScale"                  "1"
    Option "FSAADisableGamma"           "no"
    Option "FSAACustomizeMSPos"         "no"
    Option "FSAAMSPosX0"                "0.000000"
    Option "FSAAMSPosY0"                "0.000000"
    Option "FSAAMSPosX1"                "0.000000"
    Option "FSAAMSPosY1"                "0.000000"
    Option "FSAAMSPosX2"                "0.000000"
    Option "FSAAMSPosY2"                "0.000000"
    Option "FSAAMSPosX3"                "0.000000"
    Option "FSAAMSPosY3"                "0.000000"
    Option "FSAAMSPosX4"                "0.000000"
    Option "FSAAMSPosY4"                "0.000000"
    Option "FSAAMSPosX5"                "0.000000"
    Option "FSAAMSPosY5"                "0.000000"
# === Misc Options ===
    Option "UseFastTLS"                    "0"
    Option "BlockSignalsOnLock"       "on"
    Option "backingstore" "true"
    Option "UseInternalAGPGART"   "no" 
    #Option "UseInternalAGPGART"      "yes"
    Option "ForceGenericCPU"           "no"
    Option     "AGPMode" "4"
    Option     "AGPFastWrite" "True"
    Option     "EnablePageFlip" "True"
    BusID "PCI:1:0:0"    # vendor=1002, device=4e50
    Screen 0
EndSection

(in this part could be useful this last part "misc options")


i hope u can solve it, let me know

bye

---

### Post by AvvY on 2005-05-02
Ok, I tried adding agpgart to the modules file, but no luck. Just so you know exactly what error I am getting, here is a screen shot of the error message.

I had a look through your xorg.conf file but it is completly different to mine, and so I wasn't sure what would work - especially because we have different hardware configs.

Any further help is much appreciated.

Late,

---

### Post by AvvY on 2005-05-06
I still haven't been able to gain a solution to this. Is there anyway to uninstall the fglrx drivers and and then reinstalling them somehow?

Late,

---

### Post by epb613 on 2005-05-06
I had the same problem with my 9700. You have to omit xfree86-dga. This actually fixed another problem I had - whenever I would close my screen then reopen it, all my colors would get garbled.

---

