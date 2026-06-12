---
title: "Error when dim down dim down screen brightness"
date: 2012-04-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nvcnvn on 2012-04-28
I have an Dell Studio 1558, with a Mobility Radeon HD 4500/5100 Series.

After a clean install of Ubuntu 12.04, I reboot it.
And just like normal, I logged in my Ubuntu. And just like normal, the screen to bright, so I press "F4"  to dim down the display. But when I press F4 again and again immediately (to dim down the brightness to 0), **my laptop screen is turned off**, I must shut down my laptop by pressing the power button!

So I test it some more time and get the same result, I try to install the Additional Driver (ATI/AMD proprietary FGLRX), test it again, the screen not turned off but go...crazy, and I still need to shutdown my laptop.:mad:

So I think this may due to the F4 key, I install "xbacklight" and use it to dim down my screen...when I try:
```

xbacklight -set 50
xbacklight -set 40
xbacklight -set 30
xbacklight -set 20
xbacklight -set 10
xbacklight -set 0

```
I try to run these command as fast as I can (set and reset) and it still make my screen go crazy!


Is this a bug?
Is there any one get the same issue with me?

---

### Post by swartzzz on 2012-05-06
I'm also experiencing crashes/hangs when changing brightness (and also at random time).

I have Dell Studio 1558 with Intel i5 M520 CPU and AMD Mobility Radeon 5470.

Latest ubuntu 12.04 with all updates applied. I tried both the default open source driver that comes with Ubuntu as well as fglrx from AMD. In either case changing brightness hangs the machine. I was not able to install fglrx post-updates package as jockey errors out during install.

What further information can I provide to have this issue looked at?


PS. On the bright side, I'm able to take advantage of eyeFinity features of this laptop's video card. I'm able to run 3 monitors at once with Ubuntu (1x over HDMI, 1x over VGA, and the laptop screen). In Windows I can only run any 2 monitors out of the three. Dell says 3x monitors aren't supported by the videocard, AMD says I need latest drivers, but Dell no longer updates the video drivers for my laptop (haven't changed since 2010). Hence why I want to make Ubuntu work stable on this laptop.

---

### Post by Zorrothustra on 2012-06-16
Same here with Ubuntu 12.04 and Studio 1558. It crashes when dimming the display brightness. Anyone found a solution ?

---

### Post by Schinken on 2012-07-22
Same here: Dell Studio 1558 crashes and showing strange blinking patterns when trying to adjust brightness.

Though it does not crash when the power adapter is not plugged in.

---

### Post by chinthurajeev on 2012-08-13
am also experiencing these errors(when dimming brightness) with my studio1558. 
And also the system [COLOR=Red]get heated up rapidly and all process become slower[/COLOR] than the normal condition..

---

### Post by Tobeus on 2012-08-13
I may be way off base here, but I wonder if that laptop has a light sensor in it.  I would look in the bios (f2 at dell boot screen) and see if there are any settings for using the automatic light sensor.  Some of the dell laptops have that sensor and I'd bet that some linux kernels don't like playing nice with it.  If you see a setting for an automatic light sensor, try turning them off to see what happens.

I know it's not really a fix, but it could be a short-term workaround to stop a headache until the kernel drivers catch up.

Good luck either way!

-Tobeus

---

### Post by akshaynikhil on 2013-06-16
Same here. It crashed many times now it does not boots at all.

---

