---
title: "Monitor problems through gaming"
date: 2008-07-23
forum: Gaming &amp; Leisure
---

### Post by Brokentubes on 2008-07-23
I've seen that every game that I try to launch be it through Wine, or from Linux itself it tries to go full screen and upon doing so it goes way over my monitor's range... At least so says my monitor, is there anyway to fix this?

---

### Post by eragon100 on 2008-07-23
Nvidia card, probably? (but same story if you have an ATI)

Open a terminal and type sudo displayconfig-gtk

press enter

enter your password (it isn't supposed to show asterisks) and press enter

in the screen that appears, next to "Model" it likely says "Generic monitor"

click on "Generic Monitor" and select the manufacterer and model of your screen.

Select proper resulotion and refresh (you will probably have multiple options for refresh, keep trying until you find one that looks good, but DO NOT select refresh rate it was before you selected your monitor make and model, because that's the problem.)

Close the screen by clicking ok

Everything should work now, enjoy :wink:

---

### Post by Brokentubes on 2008-07-23
Well, I didn't see my monitor version under the list. (It's a HP vs17)

1280 x 1024 60hz is the settings I want, also I should point out that under
System > Preferences > Screen Resolution  It gives me a window, and in the orange box there's a smaller white box that has the word Unknown written on it.

It gives me the option to set the resolution, and refresh rate, but it's only giving me 50 and 51, and for what I know, I've never heard of no 50, 51 refresh rate, it's always been 60hz for me. Before I made the switch Windoze would tell me it is 60hz rather then 50 or 51.

~UPDATE~
I quickly went ahead and clicked on detect, it gave me a plug n' play option which allow 640 by whatever Res, and 60hz of RR.
Anyways, I booted into linux and suddenly Doom 3 was working, large then the screen, but I could see it. But I can't play at 640 by whatever..

~UPDATE2~

Now doom 3 is not even opening.

It gives me a black screen then closes.

Some help would be appreciated

---

### Post by eragon100 on 2008-07-24
You need to select the model that's most like it, my exact model also wasn't listed, but my screen works fine.

The word "unknown" is nothing to be concerned about, it also says so with my screen.

Yes, the refresh rates are strange sometimes, but just keep trying them, with one of them, everyting should work correctly. Then, keep it on that.
My refresh rate is currently 63 Hz :wink:

---

