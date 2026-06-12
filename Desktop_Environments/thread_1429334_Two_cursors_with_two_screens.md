---
title: "Two cursors with two screens"
date: 2010-03-13
forum: Desktop Environments
---

### Post by Just-trevor on 2010-03-13
My monitor set up is pictured below. The one on the left is rotated left, the one on the right is normal. The link below is a screenshot of said set up. I drew a line where they separate if you can't tell.

[http://yfrog.com/2tscreenshotsxp]("http://yfrog.com/2tscreenshotsxp")

For some reason, when I get close to the side of my big screen, a duplicate cursor shows up on the bottom of the other one. In the screenshot, the pretend cursor didn't show up, so I made a mark where it would be, and circled where the other one is. I put up the display manager for reference. 

The fake cursor is right side up, but when I move the mouse up and down, it moves right and left, and vice versa - like it's overlapping the other screen and is sideways. When the smaller screen is not rotated, there is no problem.

So has anyone had something like this happen before, or any suggestions on how to fix it?

---

### Post by asmoore82 on 2010-03-14
What's your graphics card and what does your `xrandr` look like?
```
lshw -C display
xrandr
```

---

### Post by Just-trevor on 2010-03-14
```
  *-display               
       description: VGA compatible controller
       product: RV770 [Radeon HD 4870]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:32 memory:d0000000-dfffffff(prefetchable)
       memory:f3be0000-f3beffff ioport:de00(size=256) 
       memory:f3bc0000-f3bdffff(prefetchable)
```

```
Screen 0: minimum 320 x 200, current 2944 x 1280, maximum 3200 x 3200
DFP1 connected 1920x1080+1024+200 (normal left inverted right x axis y axis) 510mm x 
287mm
   1920x1080      60.0*+
   1776x1000      60.0 +
   1680x1050      60.0 +
   1400x1050      60.0 +
   1440x900       59.9 +
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0     60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3     56.2  
   720x480        60.0  
   640x480        75.0     72.8     60.0  
   640x432        60.0  
   640x400        75.1     59.9  
   512x384        60.0     74.9  
   400x300        75.0     60.7  
   320x240        75.6     60.0  
   320x200        75.5     60.1  
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1024x1280+0+0 left (normal left inverted right
 x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1280x720       60.0 +
   1280x960       60.0  
   1152x864       75.0     60.0  
   1280x768       59.9  
   1024x768       75.0     70.1     60.0  
   800x600        72.2     75.0     70.0     60.3     56.2  
   720x480        60.0  
   640x480        75.0     72.8     60.0  
   640x432        60.0  
   640x400        75.1     59.9  
   512x384        60.0     74.9  
   400x300        75.0     60.7  
   320x240        75.6     60.0  
   320x200        75.5     60.1  
CRT2 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
COMPONENT_VIDEO disconnected (normal left inverted right x axis y axis)

```

---

### Post by asmoore82 on 2010-03-14
Wow, an ATI card, I really wasn't expecting that.

I'm unable to reproduce the problem on my Laptop with Intel GFX,
but I'm sure you get much better 3D performance out of that ATI :D.

I wanted to see `xrandr` to see if your displays really do overlap
but this doesn't seem to be the case. Perhaps it's just an ATI bug.

---

### Post by Just-trevor on 2010-03-15
I see.

Why so surprised by the ATI card? I'm surprised by your reaction.

Anyway more details if they are at all relevant: sometimes, when I boot up, the mouse is sideways and an inch or so away from where it 'actually' is, if you know what I mean. 
Problem persists if both monitors are the same resolution and if the big monitor is sideways too, but not if the small one is upside-down. (I don't know why I thought that would make a difference, but what the heck.)


Basically this monitor is not only unnecessary, but non-functional. X|

---

