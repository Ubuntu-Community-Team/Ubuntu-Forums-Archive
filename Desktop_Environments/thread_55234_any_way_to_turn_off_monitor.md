---
title: "any way to turn off monitor?"
date: 2005-08-08
forum: Desktop Environments
---

### Post by nocloud on 2005-08-08
is there a way to set kubuntu so that it turns off my monitor after a certain number of minutes?

also, when i close the lid of my laptop, i notice that the screen goes black, but the backlight stays on...

is it possible for the laptop screen to turn off when i close the lid of my laptop?

---

### Post by drizek on 2005-08-08
not sure how to do the second one, but to set it to run off the monitor after x minutes,

open konqueror and go to 

settings:/Peripherals/

then display

then click the power control tab and its pretty easy from there.

---

### Post by nocturn on 2005-08-08
[QUOTE=nocloud]is there a way to set kubuntu so that it turns off my monitor after a certain number of minutes?
[/quote]

There is an option in the KDE control center (don't remember which one)

[quote
also, when i close the lid of my laptop, i notice that the screen goes black, but the backlight stays on...

is it possible for the laptop screen to turn off when i close the lid of my laptop?[/QUOTE]

I have this too.  It seems an ACPI problem.  What laptop do you have?
What does 'xset dpms force off' do?

Mine does go off when the lid closes as the lid switch contains a hardware cut-out.

---

### Post by f1dave on 2005-08-08
Just be wary that some graphics cards/monitors are not supported with the power saving features. So if it doesn't work, there may not be much you can do about it besides (god forbid) flicking the switch or pushing the button.

---

### Post by nocloud on 2005-08-09
no hardware switch that i know of on my laptop

i have a dell inspiron 6000d btw

if anybody find a way to make the screen turn off when i close the screen, please post here and let me know

---

### Post by vendetta red on 2005-11-06
I'd also be interested in a fix for this for a Dell Inspiron 5150 with GNOME. Hibernation works, but I'd like the option of having the monitor turn off, but keeping the system running, for when I'm not away from the lappy for long. xset dpms force off does make the screen go black, but only in the sense of having a black screensaver, the monitor itself still stays on.

---

### Post by mrtenl on 2007-08-27
I have the same problem on a HP 530 laptop. I have set ac_dpms_sleep_method to "off" in the gconf-editor program, this causes the screen to turn black, and the screen backlight to turn off when i close the lid, just as i want it to do. But after a few minutes, the screen backlight turns on again for no reason. I made sure i unplugged my mouse  so there would be no input to the computer, but for some strange reason the screen won't stay black.

---

