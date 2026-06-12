---
title: "Virtual Desktop Size"
date: 2011-02-11
forum: Desktop Environments
---

### Post by Odense on 2011-02-11
I am running Ubuntu 10.10 on a Lenovo S10 netbook.
Generally it is working OK - but some programs open up with a user inter that is larger than the available screen (i.g. Handbrake).

Since I have heard I can make the Desktop larger than what is shown and scroll to see the complete interface I would like to try that.

It would be ideal for me if it was something that could be changed easily with a graphic user interface - but a command line option would also be better than nothing.

I have tried this [http://ubuntuforums.org/showthread.php?t=1139691](http://ubuntuforums.org/showthread.php?t=1139691)
but I can find neither xorg.conf or xrandr that is used in that thread
[FONT=monospace]
[/FONT]Can someone tell me how to do this - if possible a step by step (for dummies) guide ? :)

---

### Post by Odense on 2011-02-14
Really - no one have the solution ? 
That is a shame - but I suppose there is not a solution for everything - even in Ubuntu :p

---

### Post by ankspo71 on 2011-02-14
Hi,
When working with programs that don't fit the screen, you can hold down the left Alt button on your keyboard so you can drag an entire window in any direction - including moving the entire window above the screen. This works best if the window is not maximized.

Xrandr itself is a terminal application that is used to switch screen sizes, and create new screen size modes. However, Linux distros these days are very good at automatically creating all available screen size modes according to the specifications of the graphics drivers and the graphics cards - so creating a working custom screen size mode that Linux hasn't already added is rather difficult to do. 

If you were to run the command 'xrandr' in the terminal you would see this:

```
james@Kubuntu ~ $ xrandr
xrandr: Failed to get size of gamma for **output default**
**Screen 0**: minimum 320 x 240, current 1600 x 900, maximum 1600 x 900
default connected 1600x900+0+0 0mm x 0mm
   **1600x900       50.0*** 
   1440x900       51.0  
   1360x768       52.0     53.0  
   1280x720       54.0  
   1152x864       55.0     56.0     57.0     58.0  
   1024x768       59.0     60.0     61.0  
   960x600        62.0  
   960x540        63.0  
   840x525        64.0     65.0     66.0     67.0  
   832x624        68.0  
   800x600        69.0     70.0     71.0     72.0  
   720x450        73.0  
   700x525        74.0     75.0  
   680x384        76.0     77.0  
   640x480        78.0     79.0     80.0     81.0     82.0  
   512x384        83.0     84.0  
   400x300        85.0  
   320x240        86.0     87.0
```

Note that the "*" indicates both my current screen size and refresh rate.
Also note that my "Output" name is "default" and my "Screen" is "0", because you will need that info for future use of xrandr in the terminal. 
("default connected" also shows that my Output's name is default)

I am as they say "blind as a bat" if I can't find my glasses, so if I wanted to quickly change my screen size to one of the available sizes listed by xrandr, I could use the command:
```
xrandr --screen 0 -s 1360x768
```

Here is a link that covers xrandr in depth: 
[http://www.x.org/wiki/Projects/XRandR](http://www.x.org/wiki/Projects/XRandR)

In Ubuntu 10.10 (and probably earlier versions too), there are a few graphical tools for xrandr called resapplet, grandr, gnome-randr-applet, and possibly arandr. These may make switching screen sizes with xrandr easier to do.

Hope this helps.

---

### Post by Odense on 2011-02-14
Yes - the "Alt" solution is fine for me. Thank you for the help.

Thank you also for the additional explanation on randr - but to be honest I will probably revert to that if I need it for other purposes - generally I can manage on the screen size I have now :)

For me it is a problem solved :KS

---

