---
title: "Xfce4 weird window effects"
date: 2014-07-27
forum: Desktop Environments
---

### Post by Tristan_Williams on 2014-07-27
I've only noticed this in Blender 2.71 and Google Earth 7.1.2

Blender opens in Windowed mode, and maximized. Any sort of mouse movement or screen-updating (is that the right term?) creates random bursts of black areas, black lines, and invisible portions of the application interface. Any menu item that is hovered, instantly becomes invisible.

In Blender, the problem has gone away once I enter full-screen mode (which I prefer anyway)



In Google Earth, the same thing happens, but it is ALWAYS doing it. Even if I keep the mouse still and enter full-screen mode, random black lines and portions of the screen blacked out or invisible. 



What is causing this and how do I fix it?

---

### Post by mooreted on 2014-07-28
What video card do you have?

---

### Post by Tristan_Williams on 2014-07-29
> **mooreted said:**
> What video card do you have?

I don't have one. Still using the stock integrated graphics

---

### Post by mooreted on 2014-07-29
I am assuming an Intel graphics adapter. You can find out exactly what graphics adapter you have by opening a terminal and entering the following command:

lspci

If you have an Intel graphics adapter, it might help to install the Intel driver for it:

[http://www.omgubuntu.co.uk/2014/05/intel-linux-graphics-driver-installer-1-0-5](http://www.omgubuntu.co.uk/2014/05/intel-linux-graphics-driver-installer-1-0-5)

---

### Post by Tristan_Williams on 2014-07-29
```

00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)

```

---

### Post by mooreted on 2014-07-30
Not very enlightening, is it? Well, you can try installing the Intel driver from the link I posted above. You can get more information about your hardware with:

lspci -vv

or you can use lshw

It may be that your video card cannot handle heavy graphics applications, but xfce should run smoothly so I am assuming it's a video driver issue. I'll look around and see if there are any tweaks for xfce.

---

### Post by mooreted on 2014-07-30
Here is something about video tearing with Intel graphics. I had to do something similar with my Nvidia card:

[http://sn0v.wordpress.com/2013/12/17/solve-video-tearing-on-intel-ubuntu-xfce-4/](http://sn0v.wordpress.com/2013/12/17/solve-video-tearing-on-intel-ubuntu-xfce-4/)

---

### Post by Tristan_Williams on 2014-07-30
Installing the Intel driver fixed the problem

---

### Post by mooreted on 2014-07-31
> **Tristan_Williams said:**
> Installing the Intel driver fixed the problem

That's awesome. Glad you got it working.

:)

---

