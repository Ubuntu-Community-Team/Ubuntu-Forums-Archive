---
title: "[xubuntu] Using xorg.conf overrides all desktop background configuration"
date: 2014-04-21
forum: Desktop Environments
---

### Post by bluncka on 2014-04-21
I have two GPUs connected to two monitors each (four monitors total) w/ nvidia-settings creating my xorg.conf w/ Xinerama disabled & mosaic mode enabled so I can use all four displays as one continuous X screen.

When in this configuration, though, none of the desktop configuration apps (like the one to specify desktop background) are able to make any changes & the desktop background is hardcoded to use /usr/share/xfce4/backgrounds/xfce-blue.jpg.

Removing the xorg.conf allows me to modify the desktop backgrounds, but then I can't use all four monitors.  Dunno where to go from here.

---

### Post by Toz on 2014-04-21
Hello and welcome to the forums.

When in this multi-monitor configuration, are you opening the Desktop Properties applet on the desktop that you want to change the background for? If not, does that help?

Otherwise, can you post back the results of:
```
xfconf-query -c xfce4-desktop -lv
```
...when in the multi-monitor configuration.

---

### Post by bluncka on 2014-04-21
Yes - right-clicking the desktop and selecting "Desktop Settings."  It loads properly & even shows the correct background in use, but any change I make is not actually rendered on the desktop.

Output of command:
```
/backdrop/screen0/monitor0/image-path                    /usr/share/xfce4/backdrops/xubuntu-wallpaper.png
/backdrop/screen0/monitor0/image-show                    true
/backdrop/screen0/monitor0/image-style                   5
/backdrop/screen0/monitor1/image-path                    /usr/share/xfce4/backdrops/xubuntu-wallpaper.png
/backdrop/screen0/monitor1/image-show                    true
/backdrop/screen0/monitor1/image-style                   5
/backdrop/screen0/monitorDP-1/workspace0/color1          <<UNSUPPORTED>>
/backdrop/screen0/monitorDP-1/workspace0/color-style     0
/backdrop/screen0/monitorDP-1/workspace0/image-style     0
/backdrop/screen0/monitorDP-1/workspace0/last-image      /usr/share/backgrounds/xfce/xfce-blue.jpg
/backdrop/screen0/monitorDP-1/workspace1/color-style     0
/backdrop/screen0/monitorDP-1/workspace1/image-style     5
/backdrop/screen0/monitorDP-1/workspace1/last-image      /usr/share/backgrounds/xfce/xfce-blue.jpg
/backdrop/screen0/monitorDP-1/workspace2/color-style     0
/backdrop/screen0/monitorDP-1/workspace2/image-style     5
/backdrop/screen0/monitorDP-1/workspace2/last-image      /usr/share/backgrounds/xfce/xfce-blue.jpg
/backdrop/screen0/monitorDP-1/workspace3/color-style     0
/backdrop/screen0/monitorDP-1/workspace3/image-style     5
/backdrop/screen0/monitorDP-1/workspace3/last-image      /usr/share/backgrounds/xfce/xfce-blue.jpg
/backdrop/screen0/monitorDP-2/workspace0/color-style     0
/backdrop/screen0/monitorDP-2/workspace0/image-style     5
/backdrop/screen0/monitorDP-2/workspace0/last-image      /usr/share/xfce4/backdrops/xubuntu-wallpaper.png
/backdrop/screen0/monitorDP-2/workspace1/color-style     0
/backdrop/screen0/monitorDP-2/workspace1/image-style     5
/backdrop/screen0/monitorDP-2/workspace1/last-image      /usr/share/xfce4/backdrops/xubuntu-wallpaper.png
/backdrop/screen0/monitorDVI-I-1/workspace0/color1       <<UNSUPPORTED>>
/backdrop/screen0/monitorDVI-I-1/workspace0/color-style  0
/backdrop/screen0/monitorDVI-I-1/workspace0/image-style  0
/backdrop/screen0/monitorDVI-I-1/workspace0/last-image   /usr/share/xfce4/backdrops/cloudbreaker.jpg
/backdrop/screen0/monitorDVI-I-1/workspace1/color-style  0
/backdrop/screen0/monitorDVI-I-1/workspace1/image-style  5
/backdrop/screen0/monitorDVI-I-1/workspace1/last-image   /usr/share/xfce4/backdrops/xubuntu-wallpaper.png
/backdrop/screen0/monitorDVI-I-1/workspace2/color-style  0
/backdrop/screen0/monitorDVI-I-1/workspace2/image-style  5
/backdrop/screen0/monitorDVI-I-1/workspace2/last-image   /usr/share/backgrounds/xfce/xfce-blue.jpg
/backdrop/screen0/monitorDVI-I-1/workspace3/color-style  0
/backdrop/screen0/monitorDVI-I-1/workspace3/image-style  5
/backdrop/screen0/monitorDVI-I-1/workspace3/last-image   /usr/share/backgrounds/xfce/xfce-blue.jpg
/backdrop/screen1/monitorDP-1/workspace0/color-style     0
/backdrop/screen1/monitorDP-1/workspace0/image-style     5
/backdrop/screen1/monitorDP-1/workspace0/last-image      /usr/share/backgrounds/xfce/xfce-blue.jpg
/backdrop/screen1/monitorDP-1/workspace1/color-style     0
/backdrop/screen1/monitorDP-1/workspace1/image-style     5
/backdrop/screen1/monitorDP-1/workspace1/last-image      /usr/share/backgrounds/xfce/xfce-blue.jpg
/backdrop/screen1/monitorDP-1/workspace2/color-style     0
/backdrop/screen1/monitorDP-1/workspace2/image-style     5
/backdrop/screen1/monitorDP-1/workspace2/last-image      /usr/share/backgrounds/xfce/xfce-blue.jpg
/backdrop/screen1/monitorDP-1/workspace3/color-style     0
/backdrop/screen1/monitorDP-1/workspace3/image-style     5
/backdrop/screen1/monitorDP-1/workspace3/last-image      /usr/share/backgrounds/xfce/xfce-blue.jpg
/backdrop/screen1/monitorDVI-I-1/workspace0/color-style  0
/backdrop/screen1/monitorDVI-I-1/workspace0/image-style  5
/backdrop/screen1/monitorDVI-I-1/workspace0/last-image   /usr/share/backgrounds/xfce/xfce-blue.jpg
/backdrop/screen1/monitorDVI-I-1/workspace1/color-style  0
/backdrop/screen1/monitorDVI-I-1/workspace1/image-style  5
/backdrop/screen1/monitorDVI-I-1/workspace1/last-image   /usr/share/backgrounds/xfce/xfce-blue.jpg
/backdrop/screen1/monitorDVI-I-1/workspace2/color-style  0
/backdrop/screen1/monitorDVI-I-1/workspace2/image-style  5
/backdrop/screen1/monitorDVI-I-1/workspace2/last-image   /usr/share/backgrounds/xfce/xfce-blue.jpg
/backdrop/screen1/monitorDVI-I-1/workspace3/color-style  0
/backdrop/screen1/monitorDVI-I-1/workspace3/image-style  5
/backdrop/screen1/monitorDVI-I-1/workspace3/last-image   /usr/share/backgrounds/xfce/xfce-blue.jpg
/backdrop/single-workspace-mode                          true
/backdrop/single-workspace-number                        0
/desktop-icons/file-icons/show-filesystem                false
/desktop-icons/file-icons/show-home                      false
/desktop-icons/file-icons/show-removable                 false
/desktop-icons/file-icons/show-trash                     false
/desktop-icons/style                                     2
/last/window-height                                      881
/last/window-width                                       795
```

---

### Post by Toz on 2014-04-21
Can you post back the results of:
```
xrandr -q
```

Also, run this command:
```
xfconf-query -c xfce4-desktop -m
```
...and try to change one of the wallpapers on a desktop where the wallpaper changes don't work. Post back what shows up in the terminal window.

---

### Post by bluncka on 2014-04-21
```
$ xrandr -q
Screen 0: minimum 8 x 8, current 5360 x 1920, maximum 8192 x 8192
GPU-0.DVI-I-0 disconnected primary (normal left inverted right x axis y axis)
GPU-0.DVI-I-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 376mm x 301mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
GPU-0.DP-0 disconnected (normal left inverted right x axis y axis)
GPU-0.DP-1 connected 1920x1080+2360+0 (normal left inverted right x axis y axis) 475mm x 267mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
GPU-0.DP-2 disconnected (normal left inverted right x axis y axis)
GPU-0.DP-3 disconnected (normal left inverted right x axis y axis)
GPU-1.DVI-I-0 disconnected (normal left inverted right x axis y axis)
GPU-1.DVI-I-1 connected 1080x1920+1280+0 left (normal left inverted right x axis y axis) 475mm x 267mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
GPU-1.DP-0 disconnected (normal left inverted right x axis y axis)
GPU-1.DP-1 connected 1080x1920+4280+0 left (normal left inverted right x axis y axis) 475mm x 267mm
   1920x1080      60.0*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.0     60.0  
   800x600        75.0     60.3  
   640x480        75.0     59.9  
GPU-1.DP-2 disconnected (normal left inverted right x axis y axis)
GPU-1.DP-3 disconnected (normal left inverted right x axis y axis)
```

No output was generated by the xfconf-query command you provided.

---

### Post by Toz on 2014-04-21
I was hoping to find you some sort of workaround, but it doesn't look like xfdesktop is even seeing your multiple monitor setup (notice how the xfconf-query command from post 3 returns one set of display names, yet xrandr returns another). I would suggest creating a bug report for this:
```
ubuntu-bug xfdesktop4
```
...should get you started.

---

### Post by bluncka on 2014-04-21
Thanks for your help.  Bug has been opened.

---

