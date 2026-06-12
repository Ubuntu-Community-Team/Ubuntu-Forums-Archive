---
title: "Brightness control problem"
date: 2010-10-21
forum: Desktop Environments
---

### Post by shaikat on 2010-10-21
Hi All,

I am quite new in Linux and Ubuntu. I installed Ubuntu 10.04 in my Aspire 5738z Laptop. When I was using windows I can adjust my laptops brightness by pressing Fn+Left/Right arrow key. But after installing Ubuntu, it does not work. It is shown a brightness meter in the screen that is increasing/decreasing but actually the brightness does not increase/decrease.

So, Now how can I able to fix the problem.

Thanks in advance.

-Shaikat

---

### Post by jlsm on 2010-10-22
bump. I also have the same problem with my lenovo 3000 g430. The slider appears when pressing fn+up/down, but the actual display is not dimming/brightening.

I have searched other posts and threads for a solution, but none of the advised solutions are working. I've tried "xrandr --output LVDS --set BACKLIGHT_CONTROL native" and it restarted Maverick, but didn't work.

xrandr -q results were


Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
VGA1 disconnected (normal left inverted right x axis y axis)
LVDS1 connected 1280x800+0+0 (normal left inverted right x axis y axis) 303mm x 190mm
   1280x800       60.0*+
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
DP1 disconnected (normal left inverted right x axis y axis)

so I tried changing LVDS in the xrandr --output to LVDS1 which resulted in an error,

X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  11 (RRQueryOutputProperty)
  Serial number of failed request:  29
  Current serial number in output stream:  29


BTW, I installed xbacklight as another post suggested, but I don't know how to use it.

Any help would be greatly appreciated.


jlsm

---

### Post by realzippy on 2010-10-22
*BTW, I installed xbacklight as another post suggested, but I don't know how to use it.*

You have to run it from the terminal:

```
xbacklight -set 60
```

e.g. should set brightness to 60 %

---

### Post by mosaic2s on 2010-10-22
Once you are willing to check out LINUX or UBUNTU for your work, do a thorough check of the compatible hardware before making that purchase decision.
That is 99% of the work done. Balance 1% is trouble shooting.

---

### Post by shaikat on 2010-10-22
> **realzippy said:**
> *BTW, I installed xbacklight as another post suggested, but I don't know how to use it.*

You have to run it from the terminal:

```
xbacklight -set 60
```

e.g. should set brightness to 60 %

Nothing happen. :confused:

---

### Post by realzippy on 2010-10-22
seems to be a known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/489041](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/489041)

Would test the workaround *3esmit* suggests.

---

### Post by shaikat on 2010-10-23
ok I understand its a bug. The Fn+Arrow key do not work. But is there any command so that I can adjust the brightness of the monitor.

Thanks

---

