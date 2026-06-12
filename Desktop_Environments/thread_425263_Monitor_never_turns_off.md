---
title: "Monitor never turns off"
date: 2007-04-27
forum: Desktop Environments
---

### Post by schmolch on 2007-04-27
I have dpms in my xorg.conf and the xorg log says dpms is loaded ok.
I also specified 11m to turn off the monitor in the gnome-power-manager (why is 11m the miminum?)

The Screen never turns off, not even goes blank.

Specifying the standby time in xorg.conf also has no effect.

Doing xset dpms force standby works but this should not be neccessary.

Why is that?

Hardware is a coreduo laptop with intel integrated chipset.

---

### Post by schmolch on 2007-04-27
I just noticed something.

When i set the standby time to something like "xset dpms 10 20 30" it will work but something brings up the screen after a minute or so.
This means that something actively is working against dpms, what is it?

---

### Post by schmolch on 2007-04-27
Hi again,

i figured out that it is caused by the ibm_acpi module.
When i remove it DPMS behaves as expected.
I will go to the ibm_acpi list for advice.

---

### Post by schmolch on 2007-04-27
update:

Its not ibm_acpi's fault, it just provides the backlight support and whatnot.
What actually triggers the waking up of the screen is gnome-screensaver, killing it fixes the problem, even though i had it disabled in the gui-settings already.

---

### Post by Gammell on 2007-04-27
If you figure this out, I would appreciate a response. I have an R51 and ibm_acpi installed and am having a similar problem. Sometimes DPMS shuts off the screen, sometimes it doesn't... It's frustrating.

---

