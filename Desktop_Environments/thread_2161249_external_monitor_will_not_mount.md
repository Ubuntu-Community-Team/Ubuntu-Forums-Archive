---
title: "external monitor will not mount"
date: 2013-07-09
forum: Desktop Environments
---

### Post by mayagrafix on 2013-07-09
I'm using an old laptop as a e-reader so having an external monitor is essential for this task. The laptop works good with Ubuntu 12.04 2D including the external monitor but RAM is stretched thin at 512 megs. I tried to use Lubuntu in order to cut down on the RAM overhead (the only software I need is PDF Document Viewer) but could not get secondary monitor to function. After removing Lubuntu and going back to 12.04 everything works again.

Any ideas on how to get the secondary monitor going with Lubuntu?

I thought that both versions were much the same thing (Lubuntu is based on Ubuntu) but without the eye candy, but I guess not. Can I add the Ubuntu Displays control panel to the Lubuntu version? or is this not possible? (just reaching for a solution here).

I guess I can always go and buy somore RAM, however would be better if I can skate by with Lubuntu

---

### Post by jp734 on 2013-07-10
What does xrandr give you?

---

### Post by mayagrafix on 2013-07-10
The Lubuntu display control panel shows that there are two available monitors, each with its own available resolutions, and each  correctly identified by Brand name and Model number, but the external secondary monitor fails to go active and remains in stand-by mode even after switching off the "mirror image" option, and/or pressing the F5 key to turn one off and the other on.

When rebooted with Ubuntu, both monitors work perfectly.

---

### Post by jp734 on 2013-07-14
Have you looked at your xorg.0.log? What video card are you using?

---

