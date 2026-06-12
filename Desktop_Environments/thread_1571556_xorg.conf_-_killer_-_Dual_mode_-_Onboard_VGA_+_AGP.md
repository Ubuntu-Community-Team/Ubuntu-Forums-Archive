---
title: "xorg.conf - killer - Dual mode - Onboard VGA + AGP card (All old kit!)"
date: 2010-09-09
forum: Desktop Environments
---

### Post by RuniKnows on 2010-09-09
I want 2 monitors on an ancient 1G4Hz AMD that has a SiS chip-set for VGA and an ATI Rage 3D AGP card. The monitors are ancient too! I can't get both displays to work simultaneously. Nor can I get the refresh and resolutions set up at the highest level supported by either adapter/display.
 
I have modified xorg.conf following online advice. I have a file that now hangs the machine at boot up. Clearly, I've got things wrong and may well have over-baked the produce. So I need to fix it, understand what went wrong and why so. I've post the file below. Advice would be appreciated...
 
source: /etc/X11/xorg.conf
 
Section "ServerLayout"
[INDENT]Identifier "X.org Configured"
Screen 0 "Screen0" 0 0
Screen 1 "Screen1" 0 0
InputDevice "Mouse0" "CorePointer"
InputDevice "Keyboard0" "CoreKeyboard"
[/INDENT]EndSection
 
Section "Files"
[INDENT]ModulePath "/usr/lib/xorg/modules"
FontPath "/usr/share/fonts/X11/misc"
FontPath "/usr/share/fonts/X11/cyrillic"
FontPath "/usr/share/fonts/X11/100dpi/:unscaled"
FontPath "/usr/share/fonts/X11/75dpi/:unscaled"
FontPath "/usr/share/fonts/X11/Type1"
FontPath "/usr/share/fonts/X11/100dpi"
FontPath "/usr/share/fonts/X11/75dpi"
FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
FontPath "built-ins"
[/INDENT]EndSection
 
Section "Module"
[INDENT]Load "dri"
Load "glx"
Load "dbe"
Load "dri2"
Load "extmod"
Load "record"
[/INDENT]EndSection
 
Section "InputDevice"
[INDENT]Identifier "Keyboard0"
Driver "kbd"
[/INDENT]EndSection
 
Section "InputDevice"
[INDENT]Identifier "Mouse0"
Driver "mouse"
Option "Protocol" "auto"
Option "Device" "/dev/input/mice"
Option "ZAxisMapping" "4 5 6 7"
[/INDENT]EndSection
 
Section "Monitor"
[INDENT]DisplaySize 1600 x 1200 # dots x lines
Identifier "Monitor0"
VendorName "DEL"
ModelName "DELL D1025HE"
HorizSync 31.5 - 92.0
VertRefresh 50.0 - 150.0
Option "DPMS"
[/INDENT]EndSection
 
Section "Monitor"
[INDENT]DisplaySize 1280 x 1024 # dots x lines
Identifier "Monitor1"
VendorName "TAX"
ModelName "TAXAN Ergovision 735 TCO99"
HorizSync 30.0 - 92.0
VertRefresh 50.0 - 150.0
Option "DPMS"
[/INDENT]EndSection
 
Section "Device"
[INDENT]### Available Driver options are:-
### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
### [arg]: arg optional
#Option "probe_sparse" # [<bool>]
#Option "accel" # [<bool>]
#Option "crt_display" # [<bool>]
#Option "composite_sync" # [<bool>]
#Option "hw_cursor" # [<bool>]
#Option "force_pci_mode" # [<bool>]
#Option "dma_mode" # <str>
#Option "agp_mode" # <i>
#Option "agp_size" # <i>
#Option "local_textures" # [<bool>]
#Option "buffer_size" # <i>
#Option "tv_out" # [<bool>]
#Option "tv_standard" # <str>
#Option "mmio_cache" # [<bool>]
#Option "test_mmio_cache" # [<bool>]
#Option "panel_display" # [<bool>]
#Option "reference_clock" # <freq>
#Option "shadow_fb" # [<bool>]
#Option "sw_cursor" # [<bool>]
#Option "AccelMethod" # <str>
#Option "RenderAccel" # [<bool>]
Identifier "Card0"
Driver "mach64"
VendorName "ATI Technologies Inc"
BoardName "3D Rage Pro AGP 1X/2X"
BusID "PCI:0:0:0"
[/INDENT]EndSection
 
 
Section "Device"
[INDENT]Identifier "MBchipset"
Driver "sis" # vesa - SIS 630/730
VendorName "Silicon integration Systems inc."
BoardName "vga16fb.0" #Motherboard chipset
#BusID "" #platform device
[/INDENT]EndSection
 
Section "Screen"
[INDENT]Identifier "Screen0"
Device "Card0"
Monitor "Monitor0"
SubSection "Display"
Viewport 0 0
Depth 1
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 4
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 8
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 15
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 16
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1600x1200" "1280x1024" "1286x1024" "1024x768" "800x600" "640x480"
EndSubSection
[/INDENT]EndSection
 
 
Section "Screen"
[INDENT]Identifier "Screen1"
Device "MBchipset"
Monitor "Monitor1"
SubSection "Display"
Viewport 0 0
Depth 1
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 4
EndSubSection
SubSectionipse"Display"
Viewport 0 0
Depth 8
EndSubSection
SubSectionipse"Display"
Viewport 0 0
Depth 15
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 16
EndSubSection
SubSection "Display"
Viewport 0 0
Depth 24
Modes "1280x1024" "1024x768" "640x480"
EndSubSection
[/INDENT]EndSection

---

