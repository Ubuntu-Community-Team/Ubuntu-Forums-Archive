---
title: "Problem when setting resolution for 2 monitor - Ubuntu 17.04"
date: 2018-01-21
forum: Desktop Environments
---

### Post by matmachado95 on 2018-01-21
I'am using Ubuntu 17.04
[ATTACH=CONFIG]278277[/ATTACH]
My problem is that i can configure a resolution for HDMI screen, or VGA screen alone, but i cant configure it for both screens, when i try it gives me this errors:
[ATTACH=CONFIG]278278[/ATTACH][ATTACH=CONFIG]278279[/ATTACH]

this is my xrandr:
```

LVDS-1 connected primary 1366x768+1024+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768      60.00*+
   1360x768      59.80    59.96  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
VGA-1 connected 1024x768+0+282 (normal left inverted right x axis y axis) 370mm x 232mm
   1440x900      59.89 +  74.98  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1152x864      75.00  
   1024x768      75.03*   70.07    60.00  
   832x624       74.55  
   800x600       75.00    60.32    56.25  
   640x480       75.00    59.94  
   720x400       70.08  
HDMI-1 connected 1024x768+2390+0 (normal left inverted right x axis y axis) 160mm x 90mm
   1680x1050     59.95 +
   1920x1080     60.00    50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1920x1080i    60.00    50.00    59.94  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1280x800      59.91  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03*   70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
DP-1 disconnected (normal left inverted right x axis y axis)

```

This is my xrandr when connecting just 1 of my monitors:
```

Screen 0: minimum 320 x 200, current 2806 x 900, maximum 8192 x 8192
LVDS-1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768      60.00*+
   1360x768      59.80    59.96  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
VGA-1 connected 1440x900+1366+0 (normal left inverted right x axis y axis) 370mm x 232mm
   1440x900      59.89*+  74.98  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1152x864      75.00  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       75.00    60.32    56.25  
   640x480       75.00    59.94  
   720x400       70.08  
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)

```

Like you can see, i can set the recomended resolution just when using one more monitor. Never both of them. Any ideas?

---

