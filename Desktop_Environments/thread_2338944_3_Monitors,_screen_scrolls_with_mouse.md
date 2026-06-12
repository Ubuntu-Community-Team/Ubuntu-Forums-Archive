---
title: "3 Monitors, screen scrolls with mouse"
date: 2016-10-03
forum: Desktop Environments
---

### Post by pillus2 on 2016-10-03
I have been struggling with this issue for a while, my issue is that this does not always happen, and not always on every screen, but most of the time i just have to reboot a few times, and set the settings again, but today i got tired of this, and want to get into the bottom of my problem so i can fix it for good.

My setup is a Dell Latitude laptop, installed with Linux mint (also tried Ubuntu Gnome, but the same issue there), and also with other DE's.

The laptop is connected to a docking station, with 3 screens attached to it. First of all, here is the xrandr output:

```
> xrandrScreen 0: minimum 8 x 8, current 6400 x 1600, maximum 16384 x 16384
LVDS-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-2 connected primary 2560x1600+1920+0 (normal left inverted right x axis y axis) 641mm x 400mm panning 4480x1600+1920+0 tracking 6400x1600+0+0 border 0/0/0/0
   2560x1600     59.97*+
   1920x1200     59.88  
   1680x1050     59.95  
   1600x1200     60.00  
   1440x900      59.89  
   1400x1050     59.98  
   1360x765      59.85  
   1280x1024     75.02    60.02  
   1280x800      59.81  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   640x480       75.00    72.81    59.94  
DP-3 connected 1920x1200+1920+0 (normal left inverted right x axis y axis) 519mm x 324mm panning 3840x1200+0+0 tracking 6400x1600+0+0 border 0/0/0/0
   1920x1200     59.95*+  59.88  
   1920x1080     59.94  
   1680x1050     59.95  
   1440x900      59.89  
   1400x1050     59.98  
   1280x1024     60.02  
   1280x960      60.00  
   1280x800      59.81  
   1280x720      60.00    59.94  
   1024x768      60.00  
   800x600       60.32    56.25  
   720x480       59.94  
   640x480       59.94  
LVDS-1 connected
   640x480       59.94  
   320x240       60.05  
VGA-1 connected 1920x1200+4480+0 519mm x 324mm
   1920x1200     59.95*+
   1920x1080     60.00  
   1680x1050     59.95  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1280x800      59.81  
   1280x720      60.00  
   1024x768      60.00  
   800x600       60.32    56.25  
   640x480       60.00  
  640x480 (0x45) 25.175MHz -HSync -VSync
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
  1920x1200 (0x47) 154.000MHz +HSync -VSync
        h: width  1920 start 1968 end 2000 total 2080 skew    0 clock  74.04KHz
        v: height 1200 start 1203 end 1209 total 1235           clock  59.95Hz
  1680x1050 (0x49) 146.250MHz -HSync +VSync
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  1400x1050 (0x4a) 121.750MHz -HSync +VSync
        h: width  1400 start 1488 end 1632 total 1864 skew    0 clock  65.32KHz
        v: height 1050 start 1053 end 1057 total 1089           clock  59.98Hz
  1280x1024 (0x4b) 108.000MHz +HSync +VSync
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1440x900 (0x4c) 106.500MHz -HSync +VSync
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock  55.93KHz
        v: height  900 start  903 end  909 total  934           clock  59.89Hz
  1280x960 (0x4d) 108.000MHz +HSync +VSync
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock  60.00KHz
        v: height  960 start  961 end  964 total 1000           clock  60.00Hz
  1280x800 (0x4e) 83.500MHz -HSync +VSync
        h: width  1280 start 1352 end 1480 total 1680 skew    0 clock  49.70KHz
        v: height  800 start  803 end  809 total  831           clock  59.81Hz
  1280x720 (0x4f) 74.250MHz +HSync +VSync
        h: width  1280 start 1390 end 1430 total 1650 skew    0 clock  45.00KHz
        v: height  720 start  725 end  730 total  750           clock  60.00Hz
  1024x768 (0x50) 65.000MHz -HSync -VSync
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x51) 40.000MHz +HSync +VSync
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x52) 36.000MHz +HSync +VSync
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz



```

DP-3 is on the left side, with 1920x1200, middle is DP-3 with 2560x1600, and third is VGA-1 on the right side, with 1920x1200.

I normally use this command to setup when i get to work and boot up the machine:

xrandr --output DP-2 --mode 2560x1600 --output DP-3 --mode 1920x1200 --left-of DP-2 --output VGA-1 --mode 1920x1200 --right-of DP-2


All the 3 screens works just fine, the menu tab is displayed on the large screen in the middle.

Now here is my problem, which i find hard to describe.

When i place my mouse on the left monitor, and move it over to the middle monitor, i can see that whatever is on my middle screen slowly scrolls over to the left screen as well. It is like my desktop scrolls with my mouse. So if i have a terminal on the mid window, it is only displayed on the mid window, until i move my mouse to my mid window, if i move it further, to my right window, it scrolls even further and whatever i have on my mid window ends up on my left window, and whatever was on my right window moves to my middle one.

Like i mentioned, this is not always like this, but about 85% of the time, it is like it makes everything into one huge desktop, but because of the difference in resolution it gets some problems with my screen, can it be related to this?

```
Screen 0: minimum 8 x 8, current 6400 x 1600, maximum 16384 x 16384

```

If this was always a problem, then it would be less curious to me why this is, but at the time of writing, i am having constant problems and are unable to revert.

For some reason, the nvidia settings also always look like this:

[http://imgur.com/a/arDBh](http://imgur.com/a/arDBh)

Feel free to ask me if you need any more information!

UPDATE:
This seem to be a perfect description to my problem, though i only have the problem with the shifting screens, my cursor can still move between displays.
[http://askubuntu.com/questions/784434/split-windows-shifting-desktops-and-blocked-cursors-when-using-multiple-monito](http://askubuntu.com/questions/784434/split-windows-shifting-desktops-and-blocked-cursors-when-using-multiple-monito)
Though no one has mentioned a fix for this there either :(


//Pillus

---

