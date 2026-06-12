---
title: "Gnome Settings Not Showing All Available Display Resolutions"
date: 2022-09-08
forum: Desktop Environments
---

### Post by upholstery on 2022-09-08
On my Ubuntu PC, there are several resolution modes available through xrandr that are not displaying in the Settings -> Displays -> Resolution dropdown menu. The xrandr command lists these modes as available, and can successfully switch to them from the terminal, but they are not listed in the graphical menu. I would greatly appreciate some help figuring out how to add them to the dropdown menu.

Adding these resolution modes using the --newmode and --addmode parameters for xrandr does not make them available in the graphical menu.

I am running Ubuntu 22.04 LTS 64 bit on a Panasonic Toughbook CF-31 Mk. 3. My Gnome version is 42.4, and my windowing system is set to X11.

The output of the xrandr command, listing available modes, is:
```
Screen 0: minimum 320 x 200, current 1024 x 768, maximum 16384 x 16384
LVDS-1 connected primary 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00*+
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
   640x480_60.00  59.38  
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
```

Of particular interest are the listed 640x480 modes. One is the original 640x480 mode, the other(ending with "_60.00") was added using the --newmode and --addmode xrandr parameters. The graphical dropdown, however, only contains the following modes. As you can see neither 640x480 mode is available in the graphical menu.
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291013&stc=1[/IMG]
```
1024x768
1024x576
960x720
960x600
960x540
928x696
896x672
864x486
840x525
800x600
800x512
```

Despite this, running the following command ```
xrandr --output LVDS-1 --mode 640x480
``` does successfully change the display resolution, and the output of xrandr's list of modes becomes:

```
Screen 0: minimum 320 x 200, current 640 x 480, maximum 16384 x 16384
LVDS-1 connected primary 640x480+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94* 
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
   640x480_60.00  59.38  
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
```

So the 640x480 mode reported by xrandr IS a valid xrandr mode, just the graphical gnome display settings menu omits it for some reason. Does anybody know why this might be?

---

