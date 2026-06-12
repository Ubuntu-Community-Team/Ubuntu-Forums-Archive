---
title: "Issue with dual monitors and xrandr"
date: 2011-06-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by kenneho on 2011-06-29
Hi all,

I have just installed Xubuntu 11.04 on my Fujitsu Lifebook P7120, and have attached an external monitor. I wish to run a dual monitor setup, and issued this command to set it up:

```

kenneth@laptop:~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
LVDS1 connected 1280x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x768       59.8*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1024x768       75.1     75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0     59.9  
   720x400        70.1  
TV1 unknown connection (normal left inverted right x axis y axis)
   848x480        30.0 +
   640x480        30.0 +
   1024x768       30.0  
   800x600        30.0  

kenneth@laptop:~$ xrandr --output VGA1 --preferred --left-of LVDS1

```

This command enables the dual monitor setup, but what happens is that applications such as Firefox becomes kind of grayed out - it becomes very gray/dark, and I can hardly see what it displays. 

I'm quite new to xrandr, and not quite sure how to debug this thing. Any ideas as to what to try to solve this issue?

Best regards,
Kenneth

---

### Post by kenneho on 2011-07-01
I've dug a bit further, and found that dual monitors work if both monitors use the same resolution: 
```

xrandr --output LVDS1 --mode 1024x768 --right-of VGA1 --output VGA1 --mode 1024x768

```

...but when I try to use the correct resolution for both monitors, the issue comes back:
```

xrandr --output LVDS1 --mode 1280x768 --right-of VGA1 --output VGA1 --mode 1280x1024

```

Anyone got any clues as to why this doesn't work?

---

