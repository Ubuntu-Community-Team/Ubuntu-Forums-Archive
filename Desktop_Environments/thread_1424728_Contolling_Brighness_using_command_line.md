---
title: "Contolling Brighness using command line"
date: 2010-03-08
forum: Desktop Environments
---

### Post by gunjannigam on 2010-03-08
I am using Ubuntu Netbook Remix 9.04 on my Lenovo IdeaPad S10-2. I have to set brightness of screen using command line argument.
I tried various options such as
```
echo -n 40 > /proc/apci/video/OVGA/LCD/brightness 

```It changed the current value in the file to 40 from 100 but the brightness of the screen remained same.

Then I tried using 
     ```
     "xrandr --prop" 

```It said
     ```
     BACKLIGHT: 5 (0x00000005)    range:  (0,10) 

```Then I used
```

xrandr --output LVDS --set BACKLIGHT 7 

```the value changed but still the brightness of screen remained the same


Then I also tried 

     ```
     setpci -s 00:02.0 f4.b=01 

```00:02.0 was the address of VGA device returned by lspci 

It changed the value but still the brightness of screen is constant. Please help to solve ot the issue

---

