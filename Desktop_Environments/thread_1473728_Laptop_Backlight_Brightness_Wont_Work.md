---
title: "Laptop Backlight Brightness Wont Work"
date: 2010-05-05
forum: Desktop Environments
---

### Post by TheCowGod on 2010-05-05
I have an Asus P50IJ-X2 and in lucid the backlight cannot be adjusted. The panel app doesnt work, when I click on it and try to adjust the slider it just disappears. When I reopen it the slider is at the top left corner of the screen. 

The function keys seem to be detected alright, but when I press them I get the notification that the brightness is going down but nothing happens. Also after the first press the notification gets extremely laggy. If I press the brightness keys again it takes 30 seconds or more for the notification to show up. Also after the first press my volume function keys have the same behaviour in the notification area as the function keys.

Also messing with the controls in the power settings doesn't do anything. The strange thing is all of this worked perfectly in Karmic. The function keys, auto dimming, everything just worked out of the box. I have no idea where to start trouble shooting this so can anyone give me some direction?

---

### Post by TheCowGod on 2010-05-05
I just did some more poking around and found out that if I boot with the acpi_backlight=vendor option it just disables the backlight adjustment all together. The function keys now do nothing and when I launch the brightness applet it tells me that the backlight cannot be adjusted.

---

