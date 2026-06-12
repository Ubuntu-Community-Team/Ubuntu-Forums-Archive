---
title: "ATI Dual Head (Big Desktop) with fglrx"
date: 2009-01-05
forum: General Help
---

### Post by maxlem on 2009-01-05
I think I may have found (at last) a reliable solution for ATI big desktop. I'm (for the first time) able to switch resolution without restarting x, with the fglrx driver, preserving all desktop effects and stuff. Here it goes :

(Note that I have an ATI HD 3470, on a stock kubuntu 8.10 Intrepid Ibex. This card has a ~9000x9000 texture size, wich enables me to run desktop effects on such a large virtual desktop)

My monitors :
LVDS 1440x900
LCD 1680x1050 or 1280x1024 (projector) 

Here's the howto :

[SIZE="5"]_Step 1 : xorg.conf_[/SIZE]
Take blank your /etc/X11/xorg.conf file and type :
```

sudo aticonfig --initial

```

Then, edit the file :
```

sudo vi /etc/X11/xorg.conf
[...]
Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Virtual   1900 1200 #or the largest monitor you plan to plug (LVDS included)
                Depth     24
        EndSubSection
EndSection
[...]

```

I want my second display at the left of my LVDS, so I enter :
```

sudo aticonfig --dtop horizontal,reverse

```

Now, restart X.

[SIZE="5"]_Step 2 : add new resolutions:_[/SIZE]

Type :
```

sudo aticonfig --add-pairmode=1440x900+1680x1050
sudo aticonfig --add-pairmode=1440x900+1280x1024
sudo aticonfig --add-pairmode=[insert other pairmode here]

```
You should have :

```

aticonfig --list-pairmode
Get pair modes : 3
 0    1440x900 + 1680x1050 --> 3120x1050
 1    1440x900 + 1280x1024 --> 2720x1024
 2    1900x1200 + 1900x1200 --> 3800x1200

```

Remember the total resolution (e.g. 3120x1050), they correspond to xrandr modes. **NOTE : neither resolution in a pair must be more than the virtual resolution, or FGLRX won't accept it**

Now you should have all modes available in xrandr :
```

xrandr
Screen 0: minimum 320 x 200, current 1440 x 900, maximum 3800 x 1200
default connected 1440x900+0+0 0mm x 0mm                            
   3800x1200      60.0                                              
   3120x1050      60.0                                              
   2720x1024      60.0
   1440x900       60.0*    50.0
   1280x768       60.0     50.0
   1280x720       60.0     50.0
   1152x864       60.0     50.0     75.0     70.0
   1024x768       60.0     50.0     75.0     72.0     70.0
   800x600        60.0     50.0     75.0     72.0     70.0     56.0
   720x480        60.0     50.0
   640x480        60.0     50.0     75.0     72.0
   640x400        60.0     50.0     75.0
   512x384        60.0     50.0     75.0
   400x300        60.0     50.0     75.0
   320x240        60.0     50.0     75.0
   320x200        60.0     50.0     75.0
   1280x1024      75.0     70.0     60.0
   1280x960       60.0
   640x350        70.0
   1680x1050      60.0
   1400x1050      60.0


```

[SIZE="5"]_Step 3 : Enable the second monitor_[/SIZE]

If not enabled, type

```

aticonfig --enable-monitor=auto,auto

```

[SIZE="5"][U]
Step 4 : switch resolution (without X restart!)[/U][/SIZE]

Type, for example 
```

xrandr --output default --mode 1440x900 

```
  ... which gives me a single, clone display

Type :
```

xrandr --output default --mode 3120x1050

```
.. gives me big-desktop (pairmode  0    1440x900 + 1680x1050 --> 3120x1050)

Note that kwin may (and will!) complain, you may lose your background and widgets, but its a known kde4/kwin bug. as a workaround try :
```

killall plasma && sleep 1 && plasma

```

**Warning, this will reset any change you've made to widget since the last time you closed a session**

Note

---

### Post by aaaantoine on 2009-01-30
Thank you!  This helped me out a lot.

--

Running KDE 4.2, and while it seems to be better at supporting dual head than KDE 4.1, there are still a few outstanding issues.

For instance, after resizing to the single, cloned display, the windows from the second monitor remain offscreen.  Fortunately they can be moved to the visible screen by right clicking the task bar entries and selecting Move.

Also, the "pager" (workspace switcher) applet keeps the double-wide aspect ratio.

---

### Post by Linux&amp;Gsus on 2009-04-08
Hi maxlem,
I tried to follow exactly your steps but I still can't get mine to work. I run Kubuntu 8.10 as well.

My laptop screen has 1280x800 and I seem to not get anything bigger than the 800px height. Also it's always mirrored, I couldn't get 2 independent desktops.
What I try to achieve is to attach a 2nd screen (1280x1024) as well as attaching projectors with as low as 800x600px.
For kicks I, as well, would like to try the screen my wife is using, 1680x1050.

Could you potentially post your complete xorg.conf? And maybe, if you want, have a look at my original question I posted, for more info.
[http://ubuntuforums.org/showthread.php?t=1116469]("http://ubuntuforums.org/showthread.php?t=1116469")

Cheers,
L&G

---

### Post by Marsalsa on 2009-07-06
Thank u very much, this worked for me as well!

---

### Post by blackegg on 2011-03-17
Thanks,I try it,but failed.

Ubuntu 10.10 x64,ATI HD5670 ,ATI Driver 11.2 x64

Step 1 : xorg.conf
OK
Step 2 : add new resolutions:
error

What's wrong?

Step 1 : xorg.conf
CTRL + F5
sudo /etc/init.d/gdm stop
sudo aticonfig --initial
sudo vi /etc/X11/xorg.conf
sudo aticonfig --dtop horizontal,reverse
sudo /etc/init.d/gdm start

Step 2 : add new resolutions:
sudo aticonfig --add-pairmode=1660x900+1660x900
Error: pair mode is not supported when RandR 1.2 is enabled!
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.fglrx-10

---

### Post by bas89 on 2011-10-20
Same here just like Blackegg.

---

### Post by gruadp on 2011-10-20
I got it running in 11.10:

[http://www.goldfisch.at/knowwiki/howtos/ubuntu_11.10#ati-drivers](http://www.goldfisch.at/knowwiki/howtos/ubuntu_11.10#ati-drivers)

---

