---
title: "Screen resolution tool, incorrect selection"
date: 2007-03-29
forum: Desktop Environments
---

### Post by jleino on 2007-03-29
Hello!

Here's my problem: new monitor, bad resolution.

I have configured the correct values to /etc/X11/xorg.conf manually. Still
the screen resolution tool gives completely different (and incorrect) choises.
Where does it get them? Help please.

-- jleino

---

### Post by taurus on 2007-03-29
Try to reconfigure your X again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by jleino on 2007-03-29
Thanks for the reply. I tried it before tweaking the file by hand.
It may be that my on board graphics adapter is not sufficient to
drive the wanted resolution. I think Gnome resolution tool gets
its resolutions querying the driver somehow - similar as

jleino:/etc/X11$ xrandr -q
 SZ:    Pixels          Physical       Refresh
*0   1280 x 1024   ( 411mm x 258mm )  *75  
 1   1024 x 768    ( 411mm x 258mm )   75  
 2    800 x 600    ( 411mm x 258mm )   75  
 3    640 x 480    ( 411mm x 258mm )   75  
 4   1600 x 1200   ( 411mm x 258mm )   75  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none

What I would like to have is 1440x900:

xrandr -s 1440x900
Size 1440x900 not found in available modes

Perhaps I also need a new adapter, yuk Nvidia or ATI :-/

---

### Post by dcstar on 2007-03-29
> **jleino said:**
> Thanks for the reply. I tried it before tweaking the file by hand.
It may be that my on board graphics adapter is not sufficient to
drive the wanted resolution. I think Gnome resolution tool gets
its resolutions querying the driver somehow - similar as

jleino:/etc/X11$ xrandr -q
 SZ:    Pixels          Physical       Refresh
*0   1280 x 1024   ( 411mm x 258mm )  *75  
 1   1024 x 768    ( 411mm x 258mm )   75  
 2    800 x 600    ( 411mm x 258mm )   75  
 3    640 x 480    ( 411mm x 258mm )   75  
 4   1600 x 1200   ( 411mm x 258mm )   75  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - none

What I would like to have is 1440x900:

xrandr -s 1440x900
Size 1440x900 not found in available modes

Perhaps I also need a new adapter, yuk Nvidia or ATI :-/

There are posts in the forum on how to get 1440x900 resolution with manual editing of your xorg.conf file - you should probably search them out.

I know they work because I had to use them 5 days ago when I got my new 19" widescreen LCD.

---

