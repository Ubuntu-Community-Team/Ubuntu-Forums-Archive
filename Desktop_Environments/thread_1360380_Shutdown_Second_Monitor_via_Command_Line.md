---
title: "Shutdown Second Monitor via Command Line?"
date: 2009-12-20
forum: Desktop Environments
---

### Post by switchrodeo720 on 2009-12-20
I currently have a set up where my living room tv is my second monitor so I can drag video over for our family to watch. Sometimes after we're done watching the tv I find myself wanting to turn off the tv without walking over to it, but I want to ensure it doesn't turn off my main display. After researching a while, the following is the only thing I could find:
```
$ xset dpms force off
```
I think this will turn off all displays. Does anyone have a solution that will allow for a specific display to be chosen? 

Thanks in advance.

---

### Post by Isengrin on 2009-12-21
How do you set the second monitor?

If it's via xrandr, then ```
xrandr --output NAME_OF_TV --off
```

If not... sorry. xD

---

### Post by switchrodeo720 on 2009-12-21
I use nvidia-settings to configure my display settings. I'm not sure if that's independent of nvidia-settings or not.

---

### Post by switchrodeo720 on 2009-12-27
Any new ideas?

---

### Post by rhythmiccycle on 2010-01-27
you can get the name of the tv using 

```

xrandr

```

when I type it i get this

```

$ xrandr
Screen 0: minimum 320 x 200, current 1024 x 600, maximum 4096 x 4096
VGA1 connected (normal left inverted right x axis y axis)
   1360x768       59.8  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3  
   640x480        59.9  
LVDS1 connected 1024x600+0+0 (normal left inverted right x axis y axis) 220mm x 129mm
   1024x600       60.0*+
   800x600        60.3  
   640x480        59.9 

```

"VGA1" is the name given to my second monitor
"LVDS1" is the name given to my laptop screen

when you have the name of the tv you can use these codes

to turn it on and off,(i'm going to use VGA1 as the name of the TV,and LVDS1 as the name of the PC monitor. If your computer given another name to those, then replace VGA1 and/or LVDS1 with the correct name)


turn on:
```

$  xrandr --output VGA1 --auto --right-of LVDS1

```

turn off:
```

xrandr --output VGA1 --off

```

---

