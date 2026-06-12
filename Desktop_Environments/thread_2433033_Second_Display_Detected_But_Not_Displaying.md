---
title: "Second Display Detected But Not Displaying"
date: 2019-12-12
forum: Desktop Environments
---

### Post by codylamp on 2019-12-12
Both displays are detected in xrandr and in the settings GUI; however, only the primary monitor actually displays. The monitor actually goes into power saving mode after a time. This occurs in both extended and mirrored configurations. If I disable the primary monitor and choose to only display on the second monitor, the second monitor works. This configuration also works flawlessly in Windows.

The strangest behavior I've observed is after the machine is woken after sleep/suspend, occasionally the second monitor will start working without issue; however, in other instances, neither monitor works.

Relevant Details:
[LIST]
[*]Fresh installation of Ubuntu 19.10
[*]Dual Nvidia GTX 970 in SLI
[*]Monitors connected via Displayport in a daisy chain
[*]Using nvidia-driver-435
[/LIST]

```

ubuntu-desktop:~$ xrandr --queryScreen 0: minimum 8 x 8, current 4480 x 1440, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DP-0.8 connected primary 2560x1440+0+0 (normal left inverted right x axis y axis) 597mm x 336mm
   2560x1440     59.95*+
   2048x1152     60.00  
   1920x1200     59.88  
   1920x1080     60.00    59.94    50.00    29.97    25.00    23.98  
   1680x1050     59.95  
   1600x1200     60.00  
   1280x1024     75.02    60.02  
   1280x720      60.00    59.94    50.00  
   1200x960      59.90  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    59.94    59.93  
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DVI-D-0 disconnected (normal left inverted right x axis y axis)
DP-0.1 connected 1920x1200+2560+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200     59.95*+  59.88  
   1920x1080     60.00    59.94    50.00    29.97    25.00    23.98  
   1600x1200     60.00  
   1280x1024     75.02    60.02  
   1280x720      60.00    59.94    50.00  
   1152x864      75.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    59.94    59.93  
VGA-2-1 disconnected (normal left inverted right x axis y axis)
HDMI-2-1 disconnected (normal left inverted right x axis y axis)
HDMI-2-2 disconnected (normal left inverted right x axis y axis)

```

---

### Post by mörgæs on 2019-12-15
Hi, welcome to the fora.

Recently a [similar problem]("https://ubuntuforums.org/showthread.php?t=2431945&page=3&p=13916024&viewfull=1#post13916024") was solved using KDE. You could try a fresh installation of Kubuntu 19.10 for comparison.

---

