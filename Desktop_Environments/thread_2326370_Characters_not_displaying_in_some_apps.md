---
title: "Characters not displaying in some apps"
date: 2016-05-31
forum: Desktop Environments
---

### Post by boldie on 2016-05-31
This is a problem that has started after updating to 16.04. It happens sporadically - I can't identify the cause.

Characters are not displayed by certain applications such as Gedit, Tweak, Thunderbird, Nautilus, Inkscape, Gimp . A few characters may be displayed, for example c, K, t but the rest are just spaces. Different applications display different odd characters. The problem affects the window headers, menus etc as well as the content of the window. 

Other applications such as Firefox, Libreoffice are only affected in the window heading.

I can partially overcome this problem by running Tweak, choosing the fonts option and changing the text scaling factor either up or down and then characters are displayed properly. However going back to the original scaling results in the original problem. The characters in the window heading are not affected by this font scaling and are still displayed incorrectly.

I use Ubuntu Medium 12 pt and have hinting set as "slight" and anti-aliasing as RGBA. 

I can clear the problem by restarting. Is there a better way of overcoming this problem ?. Is it already recorded as a bug ?.

---

### Post by ajgreeny on 2016-05-31
What video card do you use?  What driver does that card use?

If not sure run command ```
sudo lshw -c display 
```in terminal and copy back here the output.
Please use **Code-Tags** for terminal output. See my signature below for a **How-to**

---

### Post by boldie on 2016-06-06
I don't have a video card, the system uses inbuilt Intel graphics.

The lshw output :

*-display               
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:28 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)

This appears relevant :

[http://askubuntu.com/questions/584922/how-do-i-fix-fonts-not-rendering-and-missing-letters](http://askubuntu.com/questions/584922/how-do-i-fix-fonts-not-rendering-and-missing-letters)

some people reporting this affects them in 16.04. The i915 driver is up to date according to Intel.

---

