---
title: "Dual monitor not work in ubuntu 12.04.4 LTS"
date: 2014-04-14
forum: Desktop Environments
---

### Post by sivakumar2 on 2014-04-14
Hi ,
 I have ubuntu 12.0.4 LTS  and connected  with dual monitors . It was working fine without any issues. Allof sudden  one my monitor did not give any  display . I  tried all the  troubleshooting by changing cable both vga  and DVI but  no luck. I am sure my  DVI cable is good. Even after  the   DVI cable changed ,  no output.

#lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.4 LTS
Release:	12.04
Codename:	precise

xrand  output 
#xrandr | more
Screen 0: minimum 320 x 200, current 1920 x 1200, maximum 32767 x 32767
LVDS1 connected (normal left inverted right x axis y axis)
   1440x900       60.0 +   59.9     50.0  
   1360x768       59.8     60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1920x1200+0+0 (normal left inverted right x axis y axis) 518mm x 324mm
   1920x1200      60.0*+
   1920x1080      59.9  
   1600x1200      60.0  
   1680x1050      60.0  
   1280x1024      75.0     72.0     60.0  
   1440x900       75.0     59.9  
   1024x768       75.1     70.1     60.0  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     66.0     60.0  
   720x400        70.1  
HDMI1 disconnected (normal left inverted right x axis y axis)
DP1 disconnected (normal left inverted right x axis y axis)
HDMI2 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
  1280x1024_60.00 (0xc0)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz

---

### Post by toms3d on 2014-04-15
Not sure what you did to test.  but if  you switch cables with outputs,monitor should work or not.   Or are interfaces not the same.   Do not know what kind of monitor.   crt or lcd.   lcd usually fail back light because electrolytic caps fail and backlight goes out.
Different sizes or resolutions may cause problem.  

It seems that both are 1920x1200,  But I donot claim that is defined by the output shown.

so you can also reverse right and left by this in an xterm.
xrandr --output LVDS1 --auto --right-of VGA1
or switch LVDS1 and VGA1 or use --left-of

---

