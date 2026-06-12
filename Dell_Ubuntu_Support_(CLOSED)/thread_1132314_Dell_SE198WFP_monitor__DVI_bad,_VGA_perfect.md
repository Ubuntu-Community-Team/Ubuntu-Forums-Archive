---
title: "Dell SE198WFP monitor  DVI bad, VGA perfect"
date: 2009-04-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by mikesmithv on 2009-04-21
I just purchased the Dell SE198WFP 19-inch Widescreen monitor to use with my Inspiron E1705 laptop and it works great using the VGA cable but using the DVI input it becomes an "Unrecognized Monitor".  I suspect it is just a matter of updating a database of monitor settings somewhere.  If so, who do I petition to add the specs for this monitor's DVI mode.

Here is what xrandr reports using the VGA cable:
```
Screen 0: minimum 320 x 200, current 1440 x 1800, maximum 1440 x 1813
VGA connected 1440x900+0+0 (normal left inverted right x axis y axis) 408mm x 255mm
   1440x900       59.9 +   75.0*    59.9  
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     66.7     59.9  
   720x400        70.1  
LVDS connected 1440x900+0+900 (normal left inverted right x axis y axis) 370mm x 230mm
   1440x900       59.9*+   59.9  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1 
``` 

Here is what xrandr reports using the DVI cable:
```
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 1440 x 1813
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1440x900+0+0 (normal left inverted right x axis y axis) 370mm x 230mm
   1440x900       59.9*+   59.9  
   1360x768       59.8  
   1152x864      100.0     85.1     85.0     75.0     75.0     70.0     60.0  
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TMDS-1 connected (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
```

As you can see the highest resolution using DVI is 1360 X 768 which is false.  It should be the same as VGA 1400 X 900.  I am using Jaunty and would rather not edit files to fix this, is it so close to an "all UI" configuration I would rather report this if I knew who.  Any ideas?

---

