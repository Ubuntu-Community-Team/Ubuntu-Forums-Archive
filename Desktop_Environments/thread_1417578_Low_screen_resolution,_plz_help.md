---
title: "Low screen resolution, plz help"
date: 2010-02-27
forum: Desktop Environments
---

### Post by chethan123 on 2010-02-27
Hi everyone,

I am new to Linux. I am using Ubuntu 9.10. The problem I am facing is, I am not getting higher resolution that I was getting under Windows-XP (Plz don't hate me for using Windows :) ). 

The max resolution I am getting under ubuntu is 1024x768, where as I was having 1280x1024 under windows. So I guess the problem is not with my hardware but some tweak that I am missing. So what should I do to get higher? 
Please help me out here, its the only major problem holding me back from switching to Linux completely. (U can imagine how those large icons look :(, Yak... ).

Here are tech details I thought might be useful.

uname -a ==>
Linux chethan-desktop 2.6.31-19-generic #56-Ubuntu SMP Thu Jan 28 01:26:53 UTC 2010 i686 GNU/Linux

MotherBoard==>
Intel D915GLVG (NO EXTRA GRAPHICS CARD, I AM DEPENDENT ON WHAT IS THERE ON MY MOTHER BOARD).

RAM==>
1.5 GB

Please ask for any more details you may need to analyse my situation... 

Thanks in advance.

Regards,
Chethan KR

---

### Post by talhaguy on 2010-02-27
Maybe you need to download a driver for the integrated graphics. In the main menu if you go to System > Administration > Hardware Drivers, does it say that there is a driver available?

I had low resolution too, before I downloaded the driver. But I did have an independent graphic card, so I don't know if you situation will be exactly the same.

---

### Post by Kakers on 2010-02-27
This topic might help you a bit more:
[http://ubuntuforums.org/showthread.php?t=269052](http://ubuntuforums.org/showthread.php?t=269052)

:D

---

### Post by efflandt on 2010-02-28
VGA with X often seems to default to a mode that is less than your monitor's optimum resolution, and sometimes offers modes in Display Properties that work, but are beyond its native resolution.

Look through your /var/log/Xorg.0.log to see what X is finding.  And [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) should help you test modes to find something that works.  Run **xrandr** to see what X calls your video (probably VGA1 for Intel). **cvt 1280 1024** or **gtf 1280 1024 60** may find a modeline that works.

I have not played around with xorg.conf (which does not exist by default in 9.10), but just wrote a script using xrandr commands to switch display resolutions and turn off my laptop screen when my Intel laptop is connected to HDTV.

---

### Post by chethan123 on 2010-03-01
Hey, YAHOOOOOOOOOO...............

Thank you so much guys, [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) really helped, now my comp looks so much better... 

All thanks to you guys... Ubuntu and UbuntuForum rocks... Now I am switching to ubuntu completely... 

OK, I would like to post here what I did, so ppl searching threads with similar problem would be benefited... 


1) $ xrandr -q

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 306mm x 230mm
   1024x768       75.1*    70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
   640x350        70.1  


So, this showed me that max available resolution was 1024x768. Hence decided to add undetected resolution myself. So did what 
was given under "Adding undetected resolutions".
So, second command was,

2) $ cvt 1280 1024

# 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync


After this, as given in guide, I did

3) $ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync

This executed without any error.

So I guess, new mode is created now.


Now, To check I did,

4) $ xrandr -q

Screen 0: minimum 320 x 200, current 1024 x 768, maximum 4096 x 4096
VGA1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 306mm x 230mm
   1024x768       75.1*    70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3  
   640x480        72.8     75.0     60.0  
   720x400        70.1  
   640x350        70.1  
  1280x1024_60.00 (0x11c)  109.0MHz
        h: width  1280 start 1368 end 1496 total 1712 skew    0 clock   63.7KHz
        v: height 1024 start 1027 end 1034 total 1063           clock   59.9Hz


Looks like mode is added... 



Now, the problem came... I tried to add the mode, using 

5) $ xrandr --addmode S-video 1280x1024

xrandr: cannot find output "S-video"


Looks like instead of "S-video"  I have to use VGA1 as output name... 

So did,


6) $ xrandr --addmode VGA1 1280x1024_60.00 

This executed with no problem. So guess mode added successfully :)


7) xrandr --output VGA1 --mode 1280x1024_60.00

BOOM... Screen went blank for a Sec and there it was, 1280x1028 resolution, just what I wanted... 


Now will add it to config file so that this mode will be set automatically when I login... 


-- Thank you once again guys... :)


Regards,
Chethan KR

---

### Post by jamesmk on 2010-05-08
I have the same problem as chethan123, except when I do the command:
$ xrandr --output default --mode 1280x1024_60.00

I get the error:
xrandr: Configure crtc 0 failed :-(

I know that this monitor has the 1280x1024 resolution because Window$ finds it.

Does anyone have any ideas?

---

