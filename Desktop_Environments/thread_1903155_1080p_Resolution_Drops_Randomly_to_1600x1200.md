---
title: "1080p Resolution Drops Randomly to 1600x1200"
date: 2012-01-01
forum: Desktop Environments
---

### Post by LiquidSolstice on 2012-01-01
Well, this is driving me absolutely nuts.

I have an HP Tx 2510us tablet laptop (with ATI graphics). On first install of Xubuntu, it works great, when connected to my external monitor, it properly pushes a full 1920x1080 resolution.

However, it seems every so often, it decides it doesn't like that, and it decides the new max res is going to be 1600x1200. I have spent the past two hours trying to force it back to 1920x1080 using Xrandr, and I'm at my wit's end.

The drivers were install and are working great, and this install is literally just a few days old. 

Here is what I get when I use xrandr in the terminal (I tried to follow a guide to add a resolution, which you can see at the bottom).

```
creen 0: minimum 320 x 200, current 1600 x 1200, maximum 1600 x 1600
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 260mm x 170mm
   1280x800       60.0*+
   1280x768       60.0 +
   1280x720       60.0 +
   1024x768       60.0 +
   1280x600       60.0 +
   1024x600       60.0 +
   800x600        60.0 +
   800x480        60.0 +
   720x480        60.0 +
   640x480        60.0 +
CRT1 connected 1600x1200+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1600x1200      60.0* 
   1400x1050      60.0  
   1280x1024      75.0     60.0  
   1440x900       59.9  
   1280x960       60.0  
   1280x800       75.0     60.0  
   1152x864       75.0     60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       75.0     70.1     60.0  
   1280x600       60.0  
   1024x600       60.0  
   800x600        72.2     75.0     70.0     60.3     56.2  
   800x480        60.0  
   720x480        60.0  
   640x480        75.0     72.8     60.0  
TV disconnected (normal left inverted right x axis y axis)
CV disconnected (normal left inverted right x axis y axis)
  1920x1080_60.00 (0xeb)  173.0MHz
        h: width  1920 start 2048 end 2248 total 2576 skew    0 clock   67.2KHz
        v: height 1080 start 1083 end 1088 total 1120           clock   60.0Hz

```When I use the following command (CRT1 is what my monitor identifies as):
```
xrandr --addmode CRT1 1920x1080_60.00
```This is the output:
```
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  156 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  31
  Current serial number in output stream:  32
```
For those wondering, yes, the xorg.conf file came to my mind, but this is all that is contained in it:

```

Section "Screen"
    Identifier    "Default Screen"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

```

I'm not new to Linux, but I'm kind of toying with the idea of using it fulltime, and as you can imagine, this is incredibly frustrating, so any help would be highly appreciated.

---

### Post by LiquidSolstice on 2012-01-01
So, whatever it was, I don't think I care anymore. Out of sheer desperation, I decided to check out the "Settings Editor" under the "System" menu. I found my monitor, and manually typed in a resolution of 1920x1080, and it worked great!

I don't know why Xubuntu does this, but I'll just keep this fix in mind for later.

---

