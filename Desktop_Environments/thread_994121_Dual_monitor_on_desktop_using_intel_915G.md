---
title: "Dual monitor on desktop using intel 915G"
date: 2008-11-26
forum: Desktop Environments
---

### Post by shyamsg on 2008-11-26
I had hardy --kubuntu-- before this and had dual monitors working using VGA and DVI outputs. I was using the i810 driver with Xinerama. I was using a KDE with openbox as my window decorator. This is the old xorg.conf file which worked perfectly fine. 

[COLOR="Blue"]
Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        #Load   "GLcore"
        Load    "ddc"
        Load    "dbe"
        #Load   "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier "AOC"
        Driver "i810"
        Option "MonitorLayout"  "CRT,DFP"
        Option "DDCMode" "True"
        Screen 0
        BusID "PCI:0:2:0"
EndSection

Section "Device"
        Identifier "DELL"
        Driver "i810"
        Option "MonitorLayout"  "CRT,DFP"
        Option "DDCMode" "True"
        Screen 1
        BusID "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "AOC"
        Option          "DPMS"
        HorizSync       30 - 83
        VertRefresh     56 - 76
EndSection

Section "Monitor"
        Identifier      "DELL"
        Option          "DPMS"
        HorizSync       31 - 80
        VertRefresh     56 - 76
EndSection

Section "Screen"
        Identifier      "AOC"
        Device          "AOC"
        Monitor         "AOC"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier      "DELL"
        Device          "DELL"
        Monitor         "DELL"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


Section "ServerLayout"
        Identifier      "TwoScreens"
        Screen          0 "AOC"
        Screen          1 "DELL" LeftOf "AOC"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        Option          "Xinerama" "true"
EndSection
Section "ServerFlags"
        Option          "DefaultServerLayout" "TwoScreens"
EndSection

[/COLOR]



I upgraded to intrepid and i have tried a bunch of stuff but nothing works. On top of that I read in the man screen for the driver 'intel' (i810 no longer being offered) that it does not yet support DVI output. 
I tried using both a default KDE session and the openbox session with no luck.

Any help greatly appreciated.

Shyam

---

### Post by themtx on 2008-11-26
You should be able to figure something out w/xrandr.  Here's the output from xrandr on my Intel 82Q35 Dell Optiplex 755 w/a VGA + DVI dual setup:

xrandr
Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 2560 x 1024
VGA connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0     60.0     60.0* 
   1600x1024      60.2  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     75.0     60.0     59.9  
   720x400        70.1  
TMDS-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0     60.0     60.0* 
   1600x1024      60.2  
   1440x900       59.9  
   1280x960       60.0  
   1360x768       59.8  
   1152x864       75.0     75.0     75.0     70.0     60.0  
   1024x768       75.1     75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     75.0     60.0     59.9  
   720x400        70.1 

Here's the section(s) from my xorg.conf that do the magic:

Section "Device"
	BoardName "915G"
	Driver "intel"
	Identifier "Device[0]"
	VendorName "Intel"
	Option "NoAccel" "false"
	Option "XVideo" "on"
	Option "monitor-VGA" "Monitor[1]"
        Option "monitor-TMDS-1" "Monitor[0]"
	Option "AccelMethod" "exa"
	Option "MigrationHeuristic" "greedy"
	Option "ExaNoComposite" "false"
EndSection

Section "Device"
	BoardName "915G"
	Driver "intel"
	Identifier "Device[1]"
	VendorName "Intel"
	Option "NoAccel" "false"
	Option "XVideo" "on"
	Option "monitor-VGA" "Monitor[1]"
        Option "monitor-TMDS-1" "Monitor[0]"
	Option "AccelMethod" "exa"
	Option "MigrationHeuristic" "greedy"
	Option "ExaNoComposite" "false"
EndSection

Section "Monitor"
	Identifier "Monitor[0]"
	Option "DPMS"
EndSection

Section "Monitor"
	Identifier "Monitor[1]"
	Option "DPMS"
	Option "RightOf" "Monitor[0]"
EndSection

Section "Screen"
	Device "Device[0]"
	Identifier "First"
	Monitor "Monitor[0]"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
		Virtual 2560 1024
	EndSubSection
EndSection

Section "Screen"
	Device "Device[1]"
	Identifier "Second"
	Monitor "Monitor[1]"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1280x1024"
		Virtual 2560 1024
	EndSubSection
EndSection

The BoardName "915G" section is no longer correct - but it's just a label. Could say "foo" and it wouldn't matter.  Your virtual desktop size should = (monitor 1 width (in pixels) + monitor 2 width) x height in pixels across both.  In my case it's 2 Dell 19" FPs that max out at 1280 x 1024.

good luck.

---

### Post by shyamsg on 2008-11-26
Thanks themtx.
This is a stupid question. How does xrandr decide what the maximum screen size is? 

I tried this earlier but only the login screen came up correctly. the moment the x server started, there were only 2 blank screens. I tried xrandr and it said that the max size was 1600x1600 and I am not sure that I can change that.

Shyam

---

### Post by shyamsg on 2008-12-03
I was away for the thanksgiving break. I got back and tried a couple of things to no avail. I tried what themtx was suggesting. As mentioned in the previous post, xrandr says that I have a max screen size of 1600x1600, which prevents me from using the two monitors that I have in their 1280x1024 mode. I was able to do this in the hardy setup using xinerama and i810 drivers. Is there something else that I can try?

Shyam

---

