---
title: "compiz + Unity &amp; &gt;60fps"
date: 2015-01-30
forum: Desktop Environments
---

### Post by caember on 2015-01-30
Hi,

I hope, someone can help me with this. 
The thing is, I cannot get Unity to show more than 60 fps. It seems like it is locked at that value.
For the record, I turned off 'Sync to VBlank', 'Detect Refresh Rate' and set the Refresh Rate to 144 manually in ccsm. Also 'Force independet output painting' is checked (I have 2 displays, one of which is 60fps, though it doesn't matter - it is locked to 60 even if i have only connected the 144Hz one).

xrandr:
```
Screen 0: minimum 320 x 200, current 3600 x 1093, maximum 16384 x 16384DisplayPort-0 disconnected (normal left inverted right x axis y axis)
DisplayPort-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 connected 1680x1050+1920+0 (normal left inverted right x axis y axis) 433mm x 271mm
   1680x1050      60.0*+
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     60.0  
   720x400        70.1  
DVI-0 connected primary 1920x1080+0+13 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080      60.0 +  144.0*   120.0     99.9     59.9  
   1680x1050      59.9  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x720       59.9  
   1024x768      120.0    100.0     75.1     70.1     60.0  
   832x624        74.6  
   800x600       120.0    100.0     72.2     75.0     60.3     56.2  
   640x480       120.0    100.0     75.0     72.8     66.7     60.0     59.9  
   720x400        70.1  
```

In a fullscreen app like a game, 144Hz works just fine. But as it is right now, scrolling in the browser, moving windows etc is really jerky and ugly. 

Is there any setting I didn't notice?

Edit: glxinfo | grep Open
```
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD TAHITI
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.5.0-devel
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.5.0-devel
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 10.5.0-devel
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:



```

Edit2:
Forgot to mention something: turning off Unity plugin in ccsm gives me the desired effect - so it definitely is some issue with Unity.

---

