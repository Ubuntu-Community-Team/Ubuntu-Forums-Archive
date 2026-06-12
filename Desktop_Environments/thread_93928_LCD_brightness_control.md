---
title: "LCD brightness control"
date: 2005-11-23
forum: Desktop Environments
---

### Post by mosestruong on 2005-11-23
I've just upgraded my laptop to breezy, but now, the LCD brightness control no longer work again - I can't remember what I did to make it work in Hoary - it might be after I enabled dual screen and installed another driver - but I can't find the tutorial I followed to do that.

So just wondering if anyone might know what might works. I have a Compaq Presario 2800 ATI Radeon Mobility.

Any help will be greatly appreciated!

moses

---

### Post by mosestruong on 2005-12-20
I still not too sure what the solution was - but I suspect its something to do with the xorg.conf - I had copied my old configuration file from hoary to breezy today I've tested the brightness control, and they magically worked... but I'm still not sure what exactly I did that made it work.

---

### Post by dcstar on 2005-12-20
[QUOTE=mosestruong]I've just upgraded my laptop to breezy, but now, the LCD brightness control no longer work again - I can't remember what I did to make it work in Hoary - it might be after I enabled dual screen and installed another driver - but I can't find the tutorial I followed to do that.

So just wondering if anyone might know what might works. I have a Compaq Presario 2800 ATI Radeon Mobility.

Any help will be greatly appreciated!

moses[/QUOTE]
Try fglrx.

---

### Post by mosestruong on 2006-07-17
unfortunately, fglrx only works with 8500 and newer drivers. 

I've found the solution - you need to add some option to the video device in /etc/X11/xorg.conf

For me, by adding the four options as below, I can get the brightness control to work.


```
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility M7 LW [Radeon Mobility 9000]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "RenderAccel"           "true"
        Option          "AGPMode"               "4"
        Option          "AGPFastWrite"          "true"
        Option          "EnablePageFlip"        "true"
EndSection
```

---

### Post by xyz on 2006-07-17
I'm probably off base since I'm using a Toshiba but would the following command line remind you of smth similar you did in Hoary:```
echo "brightness:1" > /proc/acpi/toshiba/lcd 

```
where the number 1 is adjustable to your wishes;i.e., 0,4,8...
Sorry if I'm off! Once in a while I see smth that would not work in my box but triggers something in my head that leads me to recalling  how I used to do it.

---

