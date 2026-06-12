---
title: "ubuntu 10.04 will no longer start with 1024x768 resolution"
date: 2010-12-01
forum: Desktop Environments
---

### Post by sundays211 on 2010-12-01
after the latest kernel update (2.6.32-26), my computer will no longer start up with a screen resolution higher than 800x600. Before this update, my computer would sometimes startup with this problem, but this could usually be fixed with a restart (or two if necessary). At this resolution the panels and a lot of tool-bars will not display properly, so I am limited as to what I can do using the GUI. 

my video card is an S3 unichrome (I think. It is built-in to the motherboard so I don't know for certain)
my screen is an old ctr one
I am running Ubuntu 10.04 on the 2.6.32-26 kernel

any help would be aprieciated

---

### Post by sundays211 on 2010-12-01
using a thread I found a while back when I had this problem, but not permanently I have entered certain commands into the terminal to get the following output:
```
sundays211@linux-desktop:~$ xrandr
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        60.0*    56.0  
   640x480        60.0  
  1024x768 (0x7c)   70.0MHz
        h: width  1024 start 1072 end 1176 total 1328 skew    0 clock   52.7KHz
        v: height  768 start  771 end  775 total  798           clock   66.1Hz
sundays211@linux-desktop:~$  $xrandr --output default --mode 1024x768_60.00 
--output: command not found
sundays211@linux-desktop:~$ xrandr --output default --mode 1024x768_70.00
xrandr: cannot find mode 1024x768_70.00
sundays211@linux-desktop:~$ xrandr --output default --mode 1024x768_60.00
xrandr: cannot find mode 1024x768_60.00
sundays211@linux-desktop:~$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
sundays211@linux-desktop:~$ xrandr --newmode "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
sundays211@linux-desktop:~$ xrandr --addmode default 1024x768_60.00
sundays211@linux-desktop:~$ xrandr --output default --mode 1024x768_60.00 
xrandr: screen cannot be larger than 800x600 (desired size 1024x768)
sundays211@linux-desktop:~$ 

``` 

not sure if it is any help, but it would help if anyone could at least give me a good idea of why this method will not work.

---

### Post by sundays211 on 2010-12-02
-

---

### Post by sundays211 on 2010-12-04
-

---

