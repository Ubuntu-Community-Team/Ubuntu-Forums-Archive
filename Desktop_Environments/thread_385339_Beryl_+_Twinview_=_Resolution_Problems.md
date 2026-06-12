---
title: "Beryl + Twinview = Resolution Problems"
date: 2007-03-15
forum: Desktop Environments
---

### Post by soapyfish on 2007-03-15
Hi,

I have recently enabled the nvidia twinview  option from within the nvidia-settings utility, 
it seemed to work as both screens are now working but for some reason the only two resolutions I can choose for the second screen are 320x240 or 640x480.

the second screen is comparible to the primary screen (both 19" CRT's  1600x1200 @ 75hz)

I have looked at my /etc/X11/xorg.conf   to see if I can work out how to set it by had but without sucess there does not seem to be a seperate screens section

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 100.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24

EndSubSection
EndSection




This is causing me some irritation after some reading I have discovered that twinview is the only supported dual display option for use with beryl (which I have the latest version of )

and help would be very much appreciated  ......thanks again to all those that brought us Ubuntu  ;-)

---

### Post by soapyfish on 2007-03-15
Ok had some more messing about I now have both screens working at the correct Resolution :D  so thats great but if I enable Beryl then I loose the window decorators :-(  I get the 3D cube though ????  

Reloading the decorators from the beryl menu does not work and neither does trying to apply another theme. 

I am reluctant to mess too much with the Beryl config as It took AGES to get it workin in the first place  !  

any help greatly recieved.  

Thanks

---

### Post by z0d on 2007-03-29
Having fixed this with soapyfish via private channels, I thought I'd upload the info we gained for future searchers. It turns out this was a compound problem; in short, we needed to stop using Xinerama, add the and use features of the nvidia driver to manually override the EDID data from both monitors, specifying the refresh rate ranges for horizontal and vertical sync. The aim was to have both screens enabled at the correct res'n and colour depth, with a specific monitor being the `primary' screen.

NOTE: This document assumes you have the nvidia proprietary drivers installed correctly.

Firstly, the earlier post referring to both monitors using the correct resolution was mis-configured using the nvidia-settings tool to choose a dual-headed Xinerama display; unforuntately, [Beryl does not currently support such displays.]("http://forum.beryl-project.org/viewtopic.php?f=54&t=1907&st=0&sk=t&sd=a&sid=2bde97bbf19488fe57c9ae159ae4cdff&start=10")

So, we needed to get both displays working correctly using the nvidia dual-display driver features. To do so, run 'gksudo nvidia-settings'. Make a menu entry or launcher on your desktop or panel if you like. Go to the "X Server Display Configuration" page. Click the `greyed out' monitor and then the "Configure" button. Select "TwinView" then arrange the screens as you like. Ensure you have a backup (see NOTES at the end) of your Xorg config file, then click "Save to X Configuration File" (what is it with all these caps?). Before you close this tool, make a note of the strings  like "DFP-0" in brackets at the end of your monitor names.

To enable ARGB GLX visuals for Beryl's use, run 'sudo nvidia-xconfig --add-argb-glx-visuals' in a command line to ensure the appropriate line(s) are added to your Xorg config file.

Now, you should have your decorators back. :KS

soapyfish & I encountered another two problems at this point;:
1) the resolutions were wrong, and setting them in the "nvidia-settings" tool had no effect
2) the wrong screen was the primary head. By "primary head", I mean the screen on which the gdm logon screen etc appear.

To fix 1), get the specs for both monitors. [URL="http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=175"]Add the following two lines in the "Device"
section[/URL] to your /etc/X11/xorg.conf file, changing the values as appropriate:
  Option "HorizSync"   "CRT-0: 50-110;  DFP-0: 40-70"
  Option "VertRefresh" "CRT-0: 60-120;  DFP-0: 60"
Change "CRT-0" and "DFP-0" to the values obtained from the "nvidia-settings" tool. (I think this problem occurred because the two CRT's were connected via BNC leads and DVI-VGA adaptors; I guess the EDID data got lost in this unusual configuration.) Change the HorizSync and VertRefresh values to those obtained from your monitor's documentaion.

To fix 2),
Add the Option
"
    Option "TwinViewXineramaInfoOrder" "DFP-0, DFP-1" with the appropriate values, see the second example below
"
:) 

NOTES:
To backup your Xorg config file, run 'sudo cp -p /etc/X11/xorg.conf /etc/X11/xorg.conf.backup_name'
To edit the xorg.conf file, you could use 'gksudo gedit /etc/X11/xorg.conf' or 'sudo vi  /etc/X11/xorg.conf', whichever you're happiest with, GUI or console.

REFERENCES:
[ Linux - Configuring Twinview (from nvidia)]("http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=175")
[Xinerama + Beryl + xrandr]("http://forum.beryl-project.org/viewtopic.php?f=54&t=1907")
[Linux - Configuring multiple x screens on one card]("http://nvidia.custhelp.com/cgi-bin/nvidia.cfg/php/enduser/std_adp.php?p_faqid=176")

EXAMPLES:
This is the "Screen" section from my xorg.conf. I have two screens, one a 17" 1280x1024 TFT and one a 15" 1024x768 TFT. I want the 17" TFT to be the `primary' display. Configuring the X server and nvidia driver this way has the bonus that you can disconnect or reconnect the second display with only having to restart the X server, not having to rewrite the configuration:
"
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
# This option, "metamodes", has NOTHING to do with the screen layout/device order
    Option         "metamodes" "CRT: 1024x768_75 +1280+0, DFP: 1280x1024_75 +0+0; DFP: 1024x768 +0+0; DFP: 800
x600 +0+0; DFP: 640x480 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
"

This is an older, but better annotated version:
"
Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
# the next line makes only the 17" TFT work
#    Option "UseDisplayDevice" "DFP-0"
# next line is for forcing the detection of connected monitors; use ONLY as a last resort!
#    Option    "ConnectedMonitor" "DFP-0,CRT-0"
# next line fixes which TFT should be the primary monitor
    Option "TwinViewXineramaInfoOrder" "DFP-0"
#
    Option "UseDisplayDevice" "DFP,CRT"
# This option, "metamodes", has NOTHING to do with the screen layout/device order
    Option         "metamodes" "CRT: 1024x768_75 +1280+0, DFP: 1280x1024_75 +0+0; CRT: 1024x768_75 +1024+0, DF
P: 1024x768 +0+0; CRT: NULL, DFP: 800x600 +0+0; CRT: NULL, DFP: 640x480 +0+0"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
"

---

### Post by soapyfish on 2007-04-17
Just to update this.

 I have performed a reinstall for various reasons and replaced the graphics card with a GeForce 8800 GTS 640mb and  this set of instructions again solved the problem I was having  with the resolution.

Installed nvidia drivers (from the nvidia page)  and all system updates from base  6.10 install

---

