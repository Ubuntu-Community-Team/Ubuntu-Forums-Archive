---
title: "Desktop still drawing for two monitors after one is gone"
date: 2010-12-10
forum: Desktop Environments
---

### Post by DiscoStu570 on 2010-12-10
Here's the skinny.  I had a dual monitor setup going for a while, then one monitor broke, and I dropped back down to one.  In some ways, the computer seems to have noticed this.  I have an NVIDIA card and the NVIDIA drivers, and in NVIDIA X Server Settings it shows only one display.  I had it configured in the Xinerama fashion, two continuous desktops side by side.

However, my desktop is still drawn as though there are two monitors, the result being that I can only see half.  This is easily apparent when I zoom out to the desktop cube.  It wouldn't be much of a serious problem, except for some reason, several important applications I use for work are popping up messages on the part of the desktop that I can't access.

I installed the latest NVIDIA drivers, hoping a driver reset might prompt whatever the problem is to go away (and it's good to do that regularly anyways) but no dice.  Anybody know what I need to modify to fix this?

---

### Post by DiscoStu570 on 2010-12-12
Just gonna give myself a little bumparino here.  I'm pretty sure this isn't an overly difficult problem to solve, anybody got a clue?

---

### Post by uriel1998 on 2010-12-13
Hm.  What does [FONT=Courier New]xrandr[/FONT] say for output?  (I'm supposing that you've already run [FONT=Courier New]xrandr --auto[/FONT] with no luck, is that right?)

---

### Post by DiscoStu570 on 2010-12-13
xrandr --auto appeared to do nothing.

The output of xrandr:
Screen 0: minimum 320 x 175, current 3200 x 1080, maximum 3200 x 1080
default connected 3200x1080+0+0 0mm x 0mm
   3200x1080      50.0* 
   1920x1080      51.0  
   1680x1050      52.0     53.0  
   1600x1024      54.0  
   1440x900       55.0  
   1400x1050      56.0     57.0     58.0  
   1360x768       59.0     60.0  
   1280x1024      61.0     62.0     63.0  
   1280x960       64.0     65.0  
   1280x720       66.0  
   1152x864       67.0     68.0     69.0     70.0     71.0     72.0     73.0  
   1024x768       74.0     75.0     76.0     77.0     78.0     79.0  
   960x720        80.0     81.0  
   960x600        82.0  
   960x540        83.0  
   928x696        84.0     85.0  
   896x672        86.0     87.0  
   840x525        88.0     89.0     90.0     91.0     92.0  
   832x624        93.0  
   800x600        94.0     95.0     96.0     97.0     98.0     99.0    100.0    101.0    102.0    103.0  
   800x512       104.0  
   720x450       105.0  
   720x400       106.0  
   700x525       107.0    108.0    109.0    110.0  
   680x384       111.0    112.0  
   640x512       113.0    114.0    115.0  
   640x480       116.0    117.0    118.0    119.0    120.0    121.0    122.0    123.0  
   640x400       124.0  
   640x350       125.0  
   576x432       126.0    127.0    128.0    129.0    130.0    131.0    132.0  
   512x384       133.0    134.0    135.0    136.0    137.0  
   416x312       138.0  
   400x300       139.0    140.0    141.0    142.0    143.0  
   360x200       144.0  
   320x240       145.0    146.0    147.0    148.0  
   320x200       149.0  
   320x175       150.0

---

### Post by uriel1998 on 2010-12-13
> **DiscoStu570 said:**
> The output of xrandr:
Screen 0: minimum 320 x 175, current 3200 x 1080, maximum 3200 x 1080
default connected 3200x1080+0+0 0mm x 0mm
   3200x1080      50.0* 


Unless you have a 3200x1080 pixel monitor, this is your problem.  For contrast, a VGA monitor I have hooked up right now:

```

Screen 0: minimum 320 x 200, current 2560 x 1024, maximum 8192 x 8192
VGA1 connected 1280x1024+1280+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  

```

(Getting pedantic for a moment in case others find this who need it.)  The output of xrandr tells you a few things:
> Screen 0: minimum 320 x 200, **current 2560 x 1024**, maximum 8192 x 8192

This is the size of your "desktop" when in a multi-monitor environment.  I've got two monitors (each 1280 px wide) sitting side by side, so, 'natch, the X width of our desktop (across both monitors) is 2560.  1024 is the height.   I could keep adding monitors (or resolution) until I hit 8192x8192.

> VGA1 connected **1280x1024**+1280+0 (normal left inverted right x axis y axis) 338mm x 270mm

This is my external monitor.  It's only 1280x1024, which is as it should be.

So for yours, it really thinks your monitor is 3200x1080, and is drawing the desktop to that size.   To hack it, try the following command (probably after reading [this page on xrandr]("http://web.archive.org/web/20080615222159/http://www.thinkwiki.org/wiki/Xorg_RandR_1.2") - it's one from the Wayback machine, but this is where I learned from - some of the things they say about Ubuntu are dated.):

```

xrandr --output default --mode 1280x800

```

**PLEASE CHANGE THE RESOLUTION (1280x800) TO YOUR MONITOR'S RESOLUTION**.  And that's a lower-case "x" there as well....

Hope that helps!

---

### Post by DiscoStu570 on 2010-12-14
Ah, yea that works.  it looks a tad fuzzy atm (1280x800 didn't work at all , said xrandr: cannot find mode 1280x800) but 1600x1024 cut it down to the right size.  I'll keep monkeying with it and find a resolution that looks right.  I knew it was drawing it for two monitors, and I knew there was some terminal command to change it, because there always is, just didn't know what it was.  Thanks for the assist :)

edit:1920x1080 looks perfect.  Not that that information is of any use to anybody else.  Just pumped from that 'I just fixed my computer's dumb problem' high.

---

### Post by uriel1998 on 2010-12-14
> **DiscoStu570 said:**
> Ah, yea that works.  it looks a tad fuzzy atm (1280x800 didn't work at all , said xrandr: cannot find mode 1280x800) but 1600x1024 cut it down to the right size.
edit:1920x1080 looks perfect.  Not that that information is of any use to anybody else.  Just pumped from that 'I just fixed my computer's dumb problem' high.

Great!  Glad to be of help - remember to mark the thread "solved"!  ;)

---

