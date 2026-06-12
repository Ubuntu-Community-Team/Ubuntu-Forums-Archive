---
title: "Ubuntu frequently freezes when external VGA monitor is used as primary display"
date: 2021-08-12
forum: Desktop Environments
---

### Post by guruao513 on 2021-08-12
Hi,

Im new to Ubuntu. Im on 20.04 LTS on my old Dell Inspiron 1545 laptop. I am trying to use my old VGA monitor as external display. Whenever I try to use it as primary display on Ubuntu, the UI freezes most of the times. There is no particular pattern, it just freezes and no actions or key strokes are recognized. The mouse pointer movement is still there. I am able to connect through ssh to this machine using ssh client as well. But nothing on the UI works until restarted.

Is this a known issue or is there a fix? Whty does it happen in the first place? Is it because of driver compatibility? Please provide some insight.
I have dual boot on this one and I do not see a similar issue when I boot into Windows 7 on the other partition. But I want to use Ubuntu for work as its more snappy on this laptop.

Thanks

---

### Post by tea for one on 2021-08-12
> **guruao513 said:**
> my old Dell Inspiron 1545 laptop. I am trying to use my old VGA monitor as external display.
How old is this hardware?
Can you supply specification details?

If the hardware is particularly old with an underpowered CPU or small RAM, then a lighter member of the Ubuntu family may be better?

---

### Post by guruao513 on 2021-08-12
> **tea for one said:**
> How old is this hardware?
Can you supply specification details?

If the hardware is particularly old with an underpowered CPU or small RAM, then a lighter member of the Ubuntu family may be better?

The hardware would be a decade old. Its Dell Inspiron 1545 with Core2Duo dual core processor and 4GB DDR2 RAM. I replaced the HDD with a SSD that runs Ubuntu and Win7 dual-boot. You think Ubuntu is heavy for this one? But it runs like charm and the issue surfaces only with the external monitor connected.

Thanks

---

### Post by tea for one on 2021-08-12
> **guruao513 said:**
> The hardware would be a decade old. Its Dell Inspiron 1545 with Core2Duo dual core processor and 4GB DDR2 RAM. I replaced the HDD with a SSD that runs Ubuntu and Win7 dual-boot. You think Ubuntu is heavy for this one? But it runs like charm and the issue surfaces only with the external monitor connected.

Thanks

I would not have mentioned that Ubuntu was possibly unsuitable for your PC if you had supplied your machine details in the original post.
Nobody had replied for 7 hours so I had a guess.

4GB RAM and an SSD would be ideal.

There should be no issue with an external VGA monitor unless there is something amiss with the connection and/or power?

What is the normal resolution of the laptop and the monitor?

---

### Post by grahammechanical on 2021-08-12
Windows 7 was released in 2009. If you was using Ubuntu 09.04 (released April 2009) you might find that Ubuntu could run a VGA monitor as well as Windows 7. Since 2009 monitors have become more capable having higher resolutions and great colour depth. Furthermore, the desktop environment and the applications have kept pace with the improvements in monitor technology.

It is possible that Ubuntu is pushing out (for want of a more technically accurate term) more graphic data than the monitor can display. It is also possible that the proprietary video driver that runs the laptop screen does not support the VGA monitor. The open source video driver might be a better choice.

Another factor to consider is the connection to the VGA monitor. What video out connector does the laptop have? D-Sub? DVi? HDMI? It could be that D-Sub does not have the bandwidth (now, there is a nice technical term :) bandwidth) to pass the graphics to the VGA monitor. Perhaps the VGA monitor is not capable of displaying the graphics from Ubuntu.

Open System Settings>Screen Display. Make sure that the listed resolution and refresh rate are not greater than the VGA monitor can cope with. Modern monitors have something called EDID (Extended Display Identification Data). It is a chip containing information about the monitor. The OS uses it to set the resolution and refresh rate. That VGA monitor may not have an EDID chip and so the resolution and refresh rate have to be set manually.

Regards

---

### Post by guruao513 on 2021-08-17
> **tea for one said:**
> I would not have mentioned that Ubuntu was possibly unsuitable for your PC if you had supplied your machine details in the original post.
Nobody had replied for 7 hours so I had a guess.

4GB RAM and an SSD would be ideal.

There should be no issue with an external VGA monitor unless there is something amiss with the connection and/or power?

What is the normal resolution of the laptop and the monitor?

Both the external monitor and built-in display are at 1366x768. Its an old Compaq R191b VGA montor and this is a supported resolution for it.

---

### Post by guruao513 on 2021-08-17
> **grahammechanical said:**
> Windows 7 was released in 2009. If you was using Ubuntu 09.04 (released April 2009) you might find that Ubuntu could run a VGA monitor as well as Windows 7. Since 2009 monitors have become more capable having higher resolutions and great colour depth. Furthermore, the desktop environment and the applications have kept pace with the improvements in monitor technology.

It is possible that Ubuntu is pushing out (for want of a more technically accurate term) more graphic data than the monitor can display. It is also possible that the proprietary video driver that runs the laptop screen does not support the VGA monitor. The open source video driver might be a better choice.

Another factor to consider is the connection to the VGA monitor. What video out connector does the laptop have? D-Sub? DVi? HDMI? It could be that D-Sub does not have the bandwidth (now, there is a nice technical term :) bandwidth) to pass the graphics to the VGA monitor. Perhaps the VGA monitor is not capable of displaying the graphics from Ubuntu.

Open System Settings>Screen Display. Make sure that the listed resolution and refresh rate are not greater than the VGA monitor can cope with. Modern monitors have something called EDID (Extended Display Identification Data). It is a chip containing information about the monitor. The OS uses it to set the resolution and refresh rate. That VGA monitor may not have an EDID chip and so the resolution and refresh rate have to be set manually.

Regards

Thanks for the insight. Its a **Compaq R191b** VGA monitor connected through the VGA port on the laptop. Neither the laptop nor the monitor have a HDMI port. I checked the resolution which is set to 1366x768 for both the inbuilt & the external display. This is a recommended resolution for this monitor.

---

