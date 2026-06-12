---
title: "visual effects"
date: 2010-07-17
forum: Desktop Environments
---

### Post by motocrossrox on 2010-07-17
how do i enable visual effects. whenever i click to enable it says searching for available driver. then it says desktop effects can not be enabled. I am trying to enable them so i can do the cube and stuff.

---

### Post by kukker32 on 2010-07-17
try search your graphic card manufacturers website for a driver for ubuntu.. or google that driver..

---

### Post by dakkar9999 on 2010-07-17
You need to activate the proprietary driver for your video card (ATI/NVIDIA).  This can be done under the menu System/Administration/Hardware drivers.

---

### Post by gordintoronto on 2010-07-17
What video card do you have? (Accessories/Terminal, lspci will show you in the line that says "VGA".

Did you try Administration/Hardware Drivers to get a proprietary video driver?

---

### Post by motocrossrox on 2010-07-22
thanks for all of your help i will try them

---

### Post by WinRiddance on 2010-07-22
If you open up a terminal screen and follow the advice of gordintoronto by typing that short command (followed by tapping your enter key) you'll possibly receive a ton of information that you can't seem to do anything with. Just look for a line that looks like this, with additional text behind it:

**VGA compatible controller:**

On my terminal, for my computer, that line looks like this:

**VGA compatible controller: ATI Technologies Inc RS780M/RS780MN [Radeon HD 3200 Graphics]**

Then go to your chipset manufacturer website, more than likely either ATI, Nvidea, or Intel, and see if they have Linux compatible drivers for your particular graphic chip. If not, then you may have to use your computer without 3D settings ... like I did for 6 months ... until the Linux compatible 3D drivers are available from either the chip manufacturer or from the Linux developers. Use the setting above 3D and if that won't work then just use the initial setting at the very top.

In closing, just to be clear, it is 100% the **responsibility of the graphic chip vendors to produce compatible Linux drivers.** But due to the strong Microsoft stranglehold in the software industry over the past 2 decades some hardware manufacturers, in particular ones for graphic chips, have just started getting their butts in gear about 3 - 5 years ago, to produce Linux compatible drivers. This will improve with every year from here on out, as Linux/Ubuntu becomes more and more popular.

If your 3D settings (whoever is reading this) work right out of the box with Ubuntu installed drivers, then that's because Linux developers are doing everything in their power to provide us with the best OS on this planet even though the hardware manufacturers are still lagging behind. Just give it some time and you'll get your 3D settings working too ....

---

