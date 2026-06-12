---
title: "External monitor not working after software update to Ubuntu 18.04"
date: 2019-03-18
forum: Desktop Environments
---

### Post by wgillett on 2019-03-18
I have a system76 Galago Pro/Intel HD 620 graphics. External monitor/HDMI has been working fine for a while. Just accepted a software update and now the laptop doesn't see the external monitor. See xrlandr output below. The key line is the last one, "HDMI-1 disconnected (normal left inverted right x axis y axis)". The monitor is getting some kind of input because it changes state when I plug the cable in, but it doesn't get a signal. Tried a different monitor, no difference. I don't have a second HDMI cable, but this failure happened immediately after the software update so thinking that is almost certainly the cause. Any ideas?

$ xrandr
Screen 0: minimum 320 x 200, current 3200 x 1800, maximum 8192 x 8192
eDP-1 connected primary 3200x1800+0+0 (normal left inverted right x axis y axis) 293mm x 165mm
   3200x1800     60.00*+  59.96    59.94    48.01  
   2880x1620     59.96    59.97  
   2560x1600     59.99    59.97  
   2560x1440     59.99    59.99    59.96    59.95  
   2048x1536     60.00  
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   2048x1152     59.99    59.98    59.90    59.91  
   1920x1200     59.88    59.95  
   1920x1080     60.01    59.97    59.96    59.93  
   1600x1200     60.00  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1600x900      59.99    59.94    59.95    59.82  
   1280x1024     60.02  
   1440x900      59.89  
   1400x900      59.96    59.88  
   1280x960      60.00  
   1440x810      60.00    59.97  
   1368x768      59.88    59.85  
   1360x768      59.80    59.96  
   1280x800      59.99    59.97    59.81    59.91  
   1152x864      60.00  
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)

---

### Post by #&amp;thj^% on 2019-03-19
GDM is well kind of buggy so if you would give this a try:
```
sudo apt install lightdm
```
next set it to use lightdm:
```
sudo dpkg-reconfigure gdm3
```
A reboot will be needed after.
You can use any display manager (LightDM, MDM, KDM, Slim, GDM)
But a heads up (Warning) if you use/choose GDM again the problem will likely return.
Good Luck

---

### Post by wgillett on 2019-03-19
Thanks for the reply! Alas, didn't work, switching to lightdm does not fix the problem.

(Noting that I actually needed to do "[COLOR=#000000][FONT=&quot]sudo dpkg-reconfigure gdm3[/FONT][/COLOR]", note "gdm3" not "gdm". I'm on Ubuntu 18.10. Had this problem on 18.04 and tried updating to 18.10 just to see if that would help.)

---

### Post by #&amp;thj^% on 2019-03-20
Sorry to hear this. And thanks for reminding me of the change in GDM && GDM3, I'm just not a Gnome user.
It also "may" help trying this in a X session instead of a wayland session.
I had to install Gnome to try this, and works for me. (Tried multiple times pulling the HDMI cable and re-plugging it. I would _not_ suggest this though )
```
xrandr
Screen 0: minimum 8 x 8, current 1600 x 900, maximum 32767 x 32767
LVDS1 connected primary 1600x900+0+0 (normal left inverted right x axis y axis) 310mm x 170mm
   1600x900      59.98*+  59.82  
   1400x900      59.96    59.88  
   1368x768      60.00    59.88    59.85  
   1280x800      59.81    59.91  
   1280x720      59.86    60.00    59.74  
   1024x768      60.00  
   1024x576      60.00    59.90    59.82  
   960x540       60.00    59.63    59.82  
   800x600       60.32    56.25  
   864x486       60.00    59.92    59.57  
   800x450       60.00  
   640x480       59.94  
   720x405       59.51    60.00    58.99  
   640x360       59.84    59.32    60.00  
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
DP3 disconnected (normal left inverted right x axis y axis)
HDMI1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
HDMI3 disconnected (normal left inverted right x axis y axis)
VGA1 connected (normal left inverted right x axis y axis)
   1920x1080     60.00 +
   1680x1050     59.95  
   1400x1050     59.98  
   1600x900      60.00  
   1280x1024     75.02    60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.95  
   1280x800      74.93    59.81  
   1152x864      75.00    59.97  
   1280x720      60.00  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   640x480       75.00    59.94  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)

```
I now have my second monitor disabled by choice here.

---

### Post by wgillett on 2019-03-21
Thanks 1fallen! Will try that and see if it helps.

---

