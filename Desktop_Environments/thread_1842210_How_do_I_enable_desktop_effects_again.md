---
title: "How do I enable desktop effects again?"
date: 2011-09-10
forum: Desktop Environments
---

### Post by palz2015 on 2011-09-10
I have tried 11.04 multiple times with no success. That aside, this time I remembered to use "Ubuntu Classic" instead of Unity because I needed to set up drivers and ccsm beforehand. I enabled the Ubuntu Unity plugin in ccsm and got my driver (nVidia 173) but it tells me that my card doesn't support Unity. When I get back to Ubuntu Classic, no effects are enabled. I disabled the Unity plugin with ccsm, but that didn't help. I used ccsm and enabled "Animations" and some window effects like "switcher" (because I used that as a test to see if the effects were working.) But it doesn't work. Is there some "Apply" button in ccsm that I'm missing? How can I get effects to work?


Edit: If you would like to solve the issue I've encountered, see the posts below and see how to force Unity and Compiz to work (only if your card is blacklisted like mine.)

---

### Post by Krytarik on 2011-09-11
Currently, you are being landed in "Ubuntu Classic (No effects)", so Compiz isn't running at all. Try following this guide to force it to run, it also covers Unity if you like to test it as well:

[http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html](http://www.tuxgarage.com/2011/05/force-unity-compiz-to-run-natty-narwhal.html)

Greetings.

---

### Post by palz2015 on 2011-09-11
Apparently my card is blacklisted. What can I do?

---

### Post by Copper Bezel on 2011-09-11
[This]("http://askubuntu.com/questions/42439/how-can-i-get-compiz-grid-working-again") help? An official Ask answer, and it looks like the same card.

Edit: removed a mistake with another similar answer specific to Unity.

---

### Post by palz2015 on 2011-09-11
OK, this forcing bypasses the blacklist. Cool. I have unity now, but the icons in the dock aren't showing up. I see the tooltip, but no icons.

---

### Post by Krytarik on 2011-09-11
Then try the "experimental" driver you hopefully get to choose in "Additional Drivers".

If not, try installing it by running:
```
sudo apt-get install libgl1-mesa-dri-experimental
```

---

### Post by palz2015 on 2011-09-11
I installed that and rebooted. Still no icons. As a side note, I like Unity a lot. It's shrinking the gap between Linux and proprietary OSes.

---

### Post by Krytarik on 2011-09-11
Check if the "nouveau" (experimental) driver is actually being run now:
```
lshw -c video
```If it's not, try removing the previously installed nvidia-173 through "Additional Drivers", and reinstall the experimental one with this command:
```
sudo apt-get install --reinstall libgl1-mesa-dri-experimental
```And nice that you like Unity, the camp is actually divided. :D

---

### Post by palz2015 on 2011-09-11
Still no icons, I lost my nVidia driver and got the one you suggested. I've been tweaking the hell out of compiz on Ubuntu Classic in the meantime ;D

---

### Post by Krytarik on 2011-09-11
The only remaining option is to try the nvidia-current driver, if you haven't done so already, and if it's offered by "Additional Drivers", too.

However, here too, you could try installing it manually:
```
sudo apt-get install nvidia-current
```
And you could also upgrade this - but not the nvidia-173 - through Ubuntu-X-Swat's PPA:

[http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html](http://www.tuxgarage.com/2011/07/upgrade-video-drivers-through-ppas.html)

---

### Post by palz2015 on 2011-09-11
Then would I remove the driver you told me about before?

---

### Post by palz2015 on 2011-09-11
Oh well, I tried that driver and now Unity goes to Ubuntu Classic (No Effects) and Ubuntu Classic has no effects. I'll reinstall that experimental one. Also, I read that the no icons thing is a bug that hasn't been fixed yet. Hmm.

---

