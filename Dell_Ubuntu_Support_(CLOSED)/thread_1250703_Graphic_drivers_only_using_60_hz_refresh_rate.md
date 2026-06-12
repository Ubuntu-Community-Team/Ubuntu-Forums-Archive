---
title: "Graphic drivers only using 60 hz refresh rate"
date: 2009-08-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jay3ld on 2009-08-26
When I installed Ubuntu 9.04, I told it to use the drivers for my graphics card (from the prompt that appears just after installtion).
I installed VirtualBox OSE, configured it to use half of my video card memory, and allowed it to use the 3d support.

I noticed now that it is only using a refresh rate of 60, in windows. I can't tell whether VirtualBox is to blame with its drivers or Ubuntu. From what I can tell, in Ubuntu for my ATI drivers, it shows under my refresh rate settings either "Preferred" or "60 hz". So I am suspecting this is an issue with Ubuntu itself.

I'm not sure on the method to get my exact video driver information. I do have the contents of my xorg.conf file though.

Any help would be appreciated in figuring this out.  Thanks.
> 
Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    DefaultDepth    24
EndSection

Section "Module"
    Load    "glx"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver    "fglrx"
EndSection

---

### Post by mikewhatever on 2009-08-27
What refresh rate do you think is appropriate for your display? Do you have a CRT or an LCD monitor?

---

### Post by jay3ld on 2009-08-27
I have a 19" flat screen lcd.

I was able to get rid of the proprietary video drivers and use the open source ones.  It finally let me select 75 hz in the display properties.

I still can't get VirtualBox although to use the 75 hz.

---

### Post by mikewhatever on 2009-08-27
60 Hz refresh rate for LCDs is actually quite common. I've seen a few 19 and 24 inch LCDs connected to computers with Windows, and having that same refresh rate. Was there a problem with the visual? Do you see a difference now?

---

### Post by Gausian on 2009-08-28
have you had a look at the specs for you lcd?  60hz is basically standard, with only the very newest lcd getting 100-120hz.

what determines the "quickness" or "quality" of your lcd is its response times.  generally between 16ms - 4ms is normal.

this is if you're using a dvi cable of course.

---

### Post by jay3ld on 2009-08-31
I may be pushing ubuntu more than I should then.

I was trying to use 75hz as when I used Virtualbox and tried to run a game, I received white boxes that would go down the screen in 3 flashes. I assumed this was due to my refresh rate from either virtual box or ubuntu.

The games I am trying to run through this are very old. 2001 and using Directx8. They semi-work,  So its cool to see them somewhat work :)

---

