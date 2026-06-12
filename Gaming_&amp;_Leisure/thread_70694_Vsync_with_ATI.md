---
title: "Vsync with ATI?"
date: 2005-09-30
forum: Gaming &amp; Leisure
---

### Post by Curlydave on 2005-09-30
Is there a way to turn on V-sync using the ATI fglrx drivers?

---

### Post by BoyOfDestiny on 2005-10-01
[QUOTE=Curlydave]Is there a way to turn on V-sync using the ATI fglrx drivers?[/QUOTE]
Yes.
I'm not at my laptop at the moment, but when you run fglrxconfig there is one point where it asks you if you would like vsync on. (I just cut and paste this info to my regular xorg.conf, since I don't want to use the one made by the ati driver)
If you still haven't done it by tomorrow, I'll post the setting from my xorg.conf (you should have luck googling it though)

---

### Post by Curlydave on 2005-10-01
Thanks for the info. I ran fglrxconfig, but for some reason it dind't change my info. Also, it's a pain resetting my mouse settings etc. I googled it and found one useful thing about making some dri config file, but it dind't work. What is the xorg setting that's needed? Thanks!

---

### Post by BoyOfDestiny on 2005-10-01
Well, this is the setting for my card... I put the one in bold that I think it is ("capabilities" is not a very good name... but I googled a bit... seems to be the one for vsync ("Synchronize buffer swap with vertical blank")
Section "Device"
Identifier                          "ATI Technologies, Inc. Radeon Mobility M300 (M22)"
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
Option "DesktopSetup"               "(null)" 
Option "ScreenOverlap"              "0" 
Option "GammaCorrectionI"           "0x00000000"
Option "GammaCorrectionII"          "0x00000000"
# === OpenGL specific profiles/settings ===
**  Option "Capabilities"               "0x00000800"**
Option "CapabilitiesEx"             "0x00000000"
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
Option "UseFastTLS"                 "0"
Option "BlockSignalsOnLock"         "on"
Option "UseInternalAGPGART"         "yes"
Option "ForceGenericCPU"            "no"
Option "KernelModuleParm"           "agplock=0" # AGP locked user pages: disabled
BusID "PCI:1:0:0"    # vendor=1002, device=5460
Screen 0
EndSection

---

