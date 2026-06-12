---
title: "Wrong default resolution"
date: 2010-05-11
forum: Desktop Environments
---

### Post by abt on 2010-05-11
Hi,

I upgraded Ubuntu a few times now (since 7.10) - and it still seems to be going well.  I really enjoy some of the new features in Lucid - Ubuntu just keeps getting better!!  I dual-boot with Windows, but I use Ubuntu much more than I do Windows :)

I have a minor problem - my resolution keeps on re-setting itself to 1440x900 rather than 1920x1200.  I think i've managed to isolate the problem.

I have a single monitor, a DELL 2408wfp.  I have the VGA and DVI connectors connected to the monitor at the same time - primarily because I could not get DVI to work under Karmic ;)  I have disabled the VGA mode, so that only DVI is being used (ie. I did this via ATI Catalyst Control Center).

When the computer boots, the screen defaults to 1440x900, on DVI.  I use ATI Catalyst Control Center to change the resolution.  Strangely enough, the ATI Catalyst Control Center tells me that 1920x1200 is the "Preferred" resolution.  I select the preferred resolution, and it stays at that resolution until I reboot.  On re-boot, the resolution changes back to 1440x900.

Suspected theory is as follows,
1. Computer starts up.  Computer says "do I have VGA signal"?  If so, display in VGA  for the BIOS setup, boot menu etc.
2. Gnome kicks in and determines it's in VGA mode.  VGA likes to use 1440x900 because it feels like it.  Computer changes resolution to 1440x900.
3. Gnome says "I should be using DVI mode, change to DVI".
4. What Lucid Lynx forgets to ask is "what resolution should I be using for DVI" - and uses the VGA resolution instead.

I tested this theory by removing the VGA cable from the monitor and re-booting.  Voilais, for the first time ever, Ubuntu booted into 1920x1200.

I don't consider my work-around to be a fix, because I'm putting wear and tear on my VGA cable - as without VGA, I don't have fall-back if the DVI display driver stops working again.

I am hoping someone can investigate my issue and see if this can be confirmed and resolved.  I appreciate any help that someone can offer :)
Sincerely,


abt

---

### Post by infamous-online on 2010-05-11
Unplug the vga cable and try it and see what happens.

---

### Post by moongia on 2010-05-11
i had a similar problem with my nvidia card and my tv.it keep booting up with a low rez.i had to type "gksu nvidia-settings" and then set my set the display the way i wanted it.it solved problem.i know you have an ATI,but maybe there an command similar to it.

---

### Post by lexen on 2011-05-26
I actually have this problem.  Does anyone know a fix?

---

