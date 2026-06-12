---
title: "Dual monitor displays only half of one"
date: 2011-01-24
forum: Desktop Environments
---

### Post by cbob on 2011-01-24
Hello,

I'm trying to use dual monitors on my unr 10.10 but when ever i have them both active(on) half(approximately) is black and unusable. Any ideas?

```
$ xrandr 
Screen 0: minimum 320 x 200, current 1880 x 1024, maximum 4096 x 4096
VGA1 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 375mm x 301mm
   1280x1024      60.0 +   75.0* 
   1280x960       75.0     70.0     60.0  
   1152x864       75.0     70.0     60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  
LVDS1 connected 1024x600+1280+0 (normal left inverted right x axis y axis) 223mm x 125mm
   1024x600       60.0*+
   800x600        60.3     56.2  
   640x480        59.9  

```regards,
cbob

---

### Post by pascaltch on 2011-01-25
hello,

last time with my laptop i have connected a second monitors on serial and after used under 10.10 system>preference>screen for config and will works !
don't know a real help for you.

cc by-nc-nd

---

### Post by cbob on 2011-01-25
I have tried to use the Monitor tool, but it show only half screen whenever I set either monitor to the left/right of each other. But when I set one below the other one, it work. Wierd...

---

### Post by cbob on 2011-02-12
Solved it self in some update..
Thanks anyway!

---

### Post by lipilee on 2011-05-05
Hi guys
I need to bump this topic as this issue just came up for me. MSI Wind U100 (VGA: Intel 945GME) with built-in 10" 1024x600 screen and an external LG doing 1440x900. If I plug the LG and set it to dual monitor mode, the LG will only have the bottom half of the screen. (Suspicion: the bottom 600 pixels of it.) This is regardless to the position of the MSI: that screen can be left, right, over, under the external one.
One more interesting thing: the top panel displays on both monitors, and also the cursor is working on the external monitor as well, even in the part that is blacked out.
Is there anything I can do/fix myself to make this work?
Thanks

---

