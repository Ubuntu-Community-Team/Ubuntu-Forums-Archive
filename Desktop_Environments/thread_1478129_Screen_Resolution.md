---
title: "Screen Resolution"
date: 2010-05-09
forum: Desktop Environments
---

### Post by W.Y.N.F.S on 2010-05-09
After upgrade to ubuntu 10.04 my screen resolution become 800x600 and in 'Monitors' I see only 2 options 800x600 and 640x480. but before upgrade I had much higher resolution

---

### Post by W.Y.N.F.S on 2010-05-09
```
deniss@deniss-desktop:~$ xrandr
Screen 0: minimum 320 x 200, current 800 x 600, maximum 4096 x 4096
VGA-0 connected 800x600+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0 +   75.0  
   1280x960       75.0     70.0     60.0  
   1152x864       75.0     70.0     60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3*    56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
S-video connected 800x600+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   800x600        59.9*+
   640x480        59.9  
deniss@deniss-desktop:~$ 

```

May be this explains something. I don`t know

---

### Post by infamous-online on 2010-05-09
What is your graphics card vendor first?

---

### Post by W.Y.N.F.S on 2010-05-12
ATI Technologies Inc RV350 AP [Radeon 9600]

---

### Post by ccprog on 2010-05-12
What is your hardware setup? There is a "S-video" marked as connected in addition to the VGA. It has the two resolutions you can see. Do you have two monitors or one monitor connected two ways?

What happens if you execute
```
xrandr --output VGA-0 --primary
```

If you are confident that your VGA connection is working properly, you could also try to run
```
xrandr --output S-video --off
```
although you might run the risk to end up with a dark screen.

---

### Post by W.Y.N.F.S on 2010-05-13
My videocard have 2 outputs VGA and DVI. I have one monitor connected to  VGA.
```
xrandr --output VGA-0 --primary
```I don`t see any changes after executing this code

Now I use Karmic Koala live cd until problem is solved, i see that Karmic koala show my monitor as AG Neovo '17' but Lucid Lynx show 'Mirror Screens' :confused:

---

### Post by W.Y.N.F.S on 2010-05-13
```
xrandr --output S-video --off
```Thank you now the problem is solved. after executing this code it show my monitor correctly, and resolutions options are back :)

---

