---
title: "lower 4:3 resolutions upscale too big on my 16:9 tv"
date: 2012-12-26
forum: Desktop Environments
---

### Post by AR_Kozz on 2012-12-26
12.04 using Gnome classic.

800x600 turns into 1280x960 with more than a third of the screen missing.

I know it is not my gpu's or fault (nvidia) or X's fault because it's set specifically to 1280x720, and all three gpu scaling options (stretch, center and aspect-ratio scale) fail to put a 1280x720 image on the screen.

I'm fairly convinced that this is another of many troubles brought by compiz's razzle-dazzle wowzer pretty graphics effects. My best guess is my session is convinced that it's got 1440 lines to work with because of the wall-of-viewports thing. But I've got all the viewport things disabled now, and everything still overscales. 

How can I tell this idiot upgrade that the TV's resolution is 1280x720 just like I told X?

---

### Post by cwsnyder on 2012-12-26
The problem is probably with a setting on your Television.  TVs don't report their EDID properly and use internal settings to get lower resolution settings to display properly.

Why don't you run your display at 1280x960 if X can show at that level?

Also can you show the results either of the output of xrandr (part of the x11-xserver-utils package) or your /etc/X11/xorg.conf file?

---

### Post by mcduck on 2012-12-26
Compiz has absolutely nothing to do with your display resolution. :D It's definitely between your graphics driver settings, and even more, with your *display's* settings.

Keep in mind that any LCD screen has one, and only one, correct resolution, ad using anything else causes the display itself to scale the image to fit the panel. So making sure you are using the display's native resolution (or one that the display is built to scale correctly)  is the first step. After that you should check that the display is set to pixel-per-pixel mode (naming depends on the manufacturer) and that all scaling is disabled. Also check if the display has geometry options, or some auto-adjust feature, that could allow you to fit the image correctly on the screen.

...and if after all that the image still isn't correct, then try looking at the settings provided by your graphics driver. They shouldn't be needed as long as you are using the correct resolution, but might be able to fix some things if the display itself simply fails to work correctly and doesn't have suitable options.

If you need more help, it would be useful to know the exact graphics card, and display, you are using. And how they are connected, of course. :)

---

### Post by AR_Kozz on 2012-12-28
I'm not going to waste time exonerating the hardware or the driver, because both performed flawlessly before I upgraded to worthless 12.04. Neither the driver nor the hardware has changed, logically then they are not at fault. The only thing different is the OS version, therefore the cause is contained in the OS. 

The tv is native 1280x720, and as I said to begin with, resolution is set to 1280x720 in Nvidia XServer Settings, instead of auto, and the same thing happens whether force-full-gps-upscale is enabled or not, regardless of the upscale type. Even under Aspect Ratio upscale type, the tv is handed a 1280x720 image with the bottom missing, instead of the 960x720 plus black bars it was given reliably in 10.04.

If it's not compiz, it's one of the countless other pointless, decorative, frivolous changes in 12.04. I've used Ubuntu since Dapper, and I'm used to having to fix everything after upgrading. But 12.04 is ridiculous.

---

### Post by cwsnyder on 2012-12-28
> **AR_Kozz said:**
> I'm not going to waste time exonerating the hardware or the driver, because both performed flawlessly before I upgraded to worthless 12.04. Neither the driver nor the hardware has changed, logically then they are not at fault. The only thing different is the OS version, therefore the cause is contained in the OS.I would tend to agree, except for one thing.  The version of X changed, which deprecated **/etc/X11/xorg.conf**.  And, yes, that is "one of the countless other pointless, decorative, frivolous changes in 12.04."

The output of the **xrandr** terminal command can show the viewport which X thinks applies to your display, as well as what X thinks is your valid video modes.  Unfortunately, **/etc/X11/xorg.conf** files have been deprecated in recent releases, and are even broken to a large extent, with the possible exception of multiple monitors.  About Ubuntu 11.04, my beautifully working xorg.conf file which set up for my 1280x1024 monitor whose EDID was not read properly and worked since installing Ubuntu 7.10 broke and splattered, never to work again.  I have had to use **xrandr** to fix the display ever since.

Assuming your monitor is read at least partially properly so that the gamma is read by your nVidia driver, you should be able to use the following lines to set the 1280x720 resolution @ 60Hz vertical refresh.```
xrandr --newmode 1280x720  74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
xrandr --addmode VGA-1 1280x720
xrandr --output VGA-1 --mode 1280x720
```The name after the **--newmode** parameter is any Linux name which you prefer for the new video mode. **VGA-1** is the parameter read from an output of **xrandr** entered on a line by itself.  My output is:```
$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 4096 x 4096
VGA-1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0  
   800x600        60.3     56.2  
   848x480        60.0  
   640x480        59.9  
   1280x1024      59.9*
```Look for the output which is **connected**.  Note my video viewport is 4096x4096.  Without the proper **xrandr** commands and parameters, the maximum resolution I can obtain is 1024x768.

---

### Post by cwsnyder on 2012-12-29
Another correction to the last post:  If your display gamma is not being read correctly, add this to the xrandr --output line:
xrandr --output <displayname> --gamma 1:1:1 --mode 1280x720

This has worked for me for 2 VirtualBox machines and a Live session, including ones which returned **default** for the <displayname>.

---

### Post by AR_Kozz on 2012-12-29
can't read the gamma but that's apparently moot because

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1280 x 720, maximum 1280 x 720
default connected 1280x720+0+0 0mm x 0mm
   1280x720       50.0* 
   960x600        51.0  
   960x540        52.0  
   840x525        53.0     54.0     55.0  
   832x624        56.0  
   800x600        57.0     58.0     59.0     60.0     61.0  
   800x512        62.0  
   720x450        63.0  
   680x384        64.0     65.0  
   640x512        66.0     67.0  
   640x480        68.0     69.0     70.0     71.0     72.0     73.0  
   576x432        74.0     75.0     76.0     77.0  
   512x384        78.0     79.0     80.0  
   416x312        81.0  
   400x300        82.0     83.0     84.0     85.0  
   320x240        86.0     87.0     88.0  

```

X still seems to know it can't go beyond 720 lines. 

So basically

) X knows 720 is the max
) the tv knows 720 is the max
) the Nvidia driver knows 720 is the max

but something else involved in fullscreen upscaling thinks the max is around 3000.

Maybe I should get this moved to multimedia and video.

---

