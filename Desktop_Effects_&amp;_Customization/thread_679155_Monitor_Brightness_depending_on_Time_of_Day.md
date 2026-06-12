---
title: "Monitor Brightness depending on Time of Day?"
date: 2008-01-26
forum: Desktop Effects &amp; Customization
---

### Post by Rhyok on 2008-01-26
Hello,
I was just wondering if there was some way to dynamically set my brightness according to what time of day it is.
For example, if I am using my computer at, let's say, 9:00 PM, I don't need to have the screen as bright as it usually is. 
How would I go about doing this?

Thanks,
rhyok

---

### Post by jpkotta on 2008-01-26
It depends.  If you have a laptop, maybe.  If you have a desktop, probably not.

---

### Post by nazeemlinux on 2008-01-27
Are you actually saying these words? :S

---

### Post by Lord Illidan on 2008-01-27
I never did it myself, but if you can configure brightness from a terminal, you can probably set up a cron script that will do it.

---

### Post by jpkotta on 2008-01-27
I suppose I should elaborate.  

I have never seen a backlight driver for an external monitor.  Not to say they are impossible.  But the driver needs to be written and the hardware has to support it.

Laptops usually do have a way to change the brightness beyond whatever the manual controls are.  Unfortunately for you, sometimes this just means extra ways for hardware to control it.  For instance, my laptop's (Dell D610) backlight is under control of the BIOS.  I can't change the settings in software.  It simply changes from one value to another when I go from battery power to ac power.  

There is a framework in the Linux kernel for backlights.  They are usually exposed to userspace in /sys/class/backlight.  If this directory is empty, there is probably no backlight support.

---

