---
title: "The Low Resolultion Problem"
date: 2010-04-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Kereltis on 2010-04-30
I managed to fix the low resolution issue a few months back after installing 9.10 on my Dell Optiplex GX 620 using Intel graphics by manually inputing the monitor into the Xorg.conf file. Yesterday I upgraded this machine to 10.04 with no problems and the resolution setting stayed the same. However when I did a fresh install on my Optiplex 745, using Intel Graphics, I had the same old low resolution problems. It was slightly better in that I could get a resolution of 1024x768 60hz, but it's still no where near what my monitor can handle, it's a 75hz monitor. After spending half the night trying different fixes and reinstall 10.04 I hooked up my GX 620 and copied the Xorg.conf to my Opitplex 745. It worked, it's not perfect but at least I now have a resolution of 1280x1024 75hz. I only have two options with resolution though. Here is my Xorg.conf for you to take a look. I hope it can help solve this problem that I was hoping 10.04 would solve as it is extremely frustrating. I love Ubuntu and think it is the best OS I have used but this problem needs to be solved! In the mean time if you own a Dell Optiplex GX 620 or 745, try copying this Xorg.conf into your own to get higher resolution. Great job on 10.04 guys but please look into this problem.

Here is the information I get about my Intel card when do** lspci -v | grep Graphics** in terminal.

00:02.0 VGA compatible controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)
00:02.1 Display controller: Intel Corporation 82Q963/Q965 Integrated Graphics Controller (rev 02)

Here's what I get when I use **xrandr** in terminal.

Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1400x1050      74.8  
   1280x1024      75.0* 
DVI1 disconnected (normal left inverted right x axis y axis)

Here is the information I get when I do    	 	 	 	 	**lshw -C video** in terminal.

 *-display:0             
       description: VGA compatible controller
       product: 82Q963/Q965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:26 memory:dfe00000-dfefffff memory:c0000000-cfffffff(prefetchable) ioport:ecb8(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: 82Q963/Q965 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:dff00000-dfffffff





                                 [SIZE=4]_**Entire Xorg.conf below**_[/SIZE]
 

 [SIZE=3]Section "ServerLayout"  [/SIZE]
 [SIZE=3]    Identifier     "X.org Configured" [/SIZE]
 [SIZE=3]    Screen      0  "Screen0" 0 0 [/SIZE]
 [SIZE=3]# commented out by update-manager, HAL is now used and auto-detects devices  [/SIZE]
 [SIZE=3]# Keyboard settings are now read from /etc/default/console-setup  [/SIZE]
 [SIZE=3]#    InputDevice    "Mouse0" "CorePointer"  [/SIZE]
 [SIZE=3]# commented out by update-manager, HAL is now used and auto-detects devices  [/SIZE]
 [SIZE=3]# Keyboard settings are now read from /etc/default/console-setup  [/SIZE]
 [SIZE=3]#    InputDevice    "Keyboard0" "CoreKeyboard"  [/SIZE]
 [SIZE=3]EndSection  [/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]Section "Files"  [/SIZE]
 [SIZE=3]    ModulePath   "/usr/lib/xorg/modules" [/SIZE]
 [SIZE=3]    FontPath     "/usr/share/fonts/X11/misc"  [/SIZE]
 [SIZE=3]    FontPath     "/usr/share/fonts/X11/cyrillic"  [/SIZE]
 [SIZE=3]    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"  [/SIZE]
 [SIZE=3]    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"  [/SIZE]
 [SIZE=3]    FontPath     "/usr/share/fonts/X11/Type1"  [/SIZE]
 [SIZE=3]    FontPath     "/usr/share/fonts/X11/100dpi"  [/SIZE]
 [SIZE=3]    FontPath     "/usr/share/fonts/X11/75dpi"  [/SIZE]
 [SIZE=3]    FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"  [/SIZE]
 [SIZE=3]    FontPath     "built-ins"  [/SIZE]
 [SIZE=3]EndSection  [/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]Section "Module"  [/SIZE]
 [SIZE=3]    Load  "glx"  [/SIZE]
 [SIZE=3]    Load  "extmod"  [/SIZE]
 [SIZE=3]    Load  "dbe"  [/SIZE]
 [SIZE=3]    Load  "dri2"  [/SIZE]
 [SIZE=3]    Load  "dri"  [/SIZE]
 [SIZE=3]    Load  "record"  [/SIZE]
 [SIZE=3]EndSection  [/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]# commented out by update-manager, HAL is now used and auto-detects devices  [/SIZE]
 [SIZE=3]# Keyboard settings are now read from /etc/default/console-setup  [/SIZE]
 [SIZE=3]#Section "InputDevice"  [/SIZE]
 [SIZE=3]#    Identifier  "Keyboard0"  [/SIZE]
 [SIZE=3]#    Driver      "kbd"  [/SIZE]
 [SIZE=3]#EndSection  [/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]# commented out by update-manager, HAL is now used and auto-detects devices  [/SIZE]
 [SIZE=3]# Keyboard settings are now read from /etc/default/console-setup  [/SIZE]
 [SIZE=3]#Section "InputDevice"  [/SIZE]
 [SIZE=3]#    Identifier  "Mouse0"  [/SIZE]
 [SIZE=3]#    Driver      "mouse"  [/SIZE]
 [SIZE=3]#    Option        "Protocol" "auto"  [/SIZE]
 [SIZE=3]#    Option        "Device" "/dev/input/mice"  [/SIZE]
 [SIZE=3]#    Option        "ZAxisMapping" "4 5 6 7"  [/SIZE]
 [SIZE=3]#EndSection  [/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]Section "Monitor"  [/SIZE]
 [SIZE=3]    Identifier   "Monitor0"  [/SIZE]
 [SIZE=3]        HorizSync     76.00 - 81.00  [/SIZE]
 [SIZE=3]        VertRefresh   75.0  [/SIZE]
 [SIZE=3]        VendorName   "Lenova" [/SIZE]
 [SIZE=3]    ModelName    "L1900p"  [/SIZE]
 [SIZE=3]EndSection  [/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]Section "Device"  [/SIZE]
 [SIZE=3]        ### Available Driver options are:-  [/SIZE]
 [SIZE=3]        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",  [/SIZE]
 [SIZE=3]        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"  [/SIZE]
 [SIZE=3]        ### [arg]: arg optional  [/SIZE]
 [SIZE=3]        #Option     "NoAccel"                # [<bool>]  [/SIZE]
 [SIZE=3]        #Option     "SWcursor"               # [<bool>]  [/SIZE]
 [SIZE=3]        #Option     "ColorKey"               # <i>  [/SIZE]
 [SIZE=3]        #Option     "CacheLines"             # <i>  [/SIZE]
 [SIZE=3]        #Option     "Dac6Bit"                # [<bool>]  [/SIZE]
 [SIZE=3]        #Option     "DRI"                    # [<bool>]  [/SIZE]
 [SIZE=3]        #Option     "NoDDC"                  # [<bool>]  [/SIZE]
 [SIZE=3]        #Option     "ShowCache"              # [<bool>]  [/SIZE]
 [SIZE=3]        #Option     "XvMCSurfaces"           # <i>  [/SIZE]
 [SIZE=3]        #Option     "PageFlip"               # [<bool>]  [/SIZE]
 [SIZE=3]    Identifier  "Card0"  [/SIZE]
 [SIZE=3]    Driver      "intel"  [/SIZE]
 [SIZE=3]    VendorName  "Intel Corporation" [/SIZE]
 [SIZE=3]    BoardName   "82945G/GZ Integrated Graphics Controller"  [/SIZE]
 [SIZE=3]    BusID       "PCI:0:2:0"  [/SIZE]
 [SIZE=3]EndSection  [/SIZE]
 [SIZE=3]
[/SIZE] 
 [SIZE=3]Section "Screen"  [/SIZE]
 [SIZE=3]    Identifier "Screen0"  [/SIZE]
 [SIZE=3]    Device     "Card0"  [/SIZE]
 [SIZE=3]    Monitor    "Monitor0"  [/SIZE]
 [SIZE=3]    SubSection "Display"  [/SIZE]
 [SIZE=3]        Viewport   0 0  [/SIZE]
 [SIZE=3]        Depth     1  [/SIZE]
 [SIZE=3]    EndSubSection  [/SIZE]
 [SIZE=3]    SubSection "Display"  [/SIZE]
 [SIZE=3]        Viewport   0 0  [/SIZE]
 [SIZE=3]        Depth     4  [/SIZE]
 [SIZE=3]    EndSubSection  [/SIZE]
 [SIZE=3]    SubSection "Display"  [/SIZE]
 [SIZE=3]        Viewport   0 0  [/SIZE]
 [SIZE=3]        Depth     8  [/SIZE]
 [SIZE=3]    EndSubSection  [/SIZE]
 [SIZE=3]    SubSection "Display"  [/SIZE]
 [SIZE=3]        Viewport   0 0  [/SIZE]
 [SIZE=3]        Depth     15  [/SIZE]
 [SIZE=3]    EndSubSection  [/SIZE]
 [SIZE=3]    SubSection "Display"  [/SIZE]
 [SIZE=3]        Viewport   0 0  [/SIZE]
 [SIZE=3]        Depth     16  [/SIZE]
 [SIZE=3]    EndSubSection  [/SIZE]
 [SIZE=3]    SubSection "Display"  [/SIZE]
 [SIZE=3]        Viewport   0 0  [/SIZE]
 [SIZE=3]        Depth     24  [/SIZE]
 [SIZE=3]    EndSubSection  [/SIZE]
 [SIZE=3]EndSection  [/SIZE]

---

### Post by Kereltis on 2011-01-17
I think I have solved the low resolution problem for Nvidia cards. I've tested this with an Asus Nvidia 8800GT. Yesterday I installed an 8800GT on an old PC I had but when I installed Ubuntu 10.10 I had the same old low resolution problem. My monitor is an old Dell analog LCD 4:3 ratio and I was using a vga to DVI-I adapter (digital & analog signal). No luck, I still had resolution problems but this time I knew the 8800GT worked because I had previously tested it in another PC using Ubuntu 10.04 and it detected my monitor perfectly. So this time I swapped the vga to DVI-I adapter for a vga to DVI-A (analog only signal), rebooted and it worked, when Ubuntu started up the Nvidia drivers detected my monitor perfectly. Hope this helps all the frustrated people out there. The DVI-A adapter is the one that looks like it's missing pins, that's because it doesn't use the digital signal, so check your vga to dvi adapter if your monitor is not being detected.

It's strange because the the vga to DVI-I adapter is supposed to be good for both analog and digital monitors but it didn't work for me and I tried 2 different ones that I know work.

---

