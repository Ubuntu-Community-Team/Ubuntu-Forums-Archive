---
title: "screen resolution manager"
date: 2008-03-09
forum: Desktop Environments
---

### Post by Ginger Towel on 2008-03-09
I want my screen res to be at 1280x960 @ 56Hz so i set it to that in the screens and graphics section of the System>>Administration. when i restart my computer it gets automatically set to 1280x1024 @ 51Hz. which does not work on my monitor, it becomes off center with black borders and i cannot see part of my desktop.

how can i set it to save the 1280x960 @ 56Hz setting?

---

### Post by taurus on 2008-03-09
What kind of graphic card do you have in that machine?

---

### Post by Ginger Towel on 2008-03-09
i have a GeForce 7950 GT

and a 32" Vizio monitor/TV

---

### Post by taurus on 2008-03-09
Have you installed an nvidia restricted driver for your graphic card?  Look in System -> Administration -> Restricted Drivers Manager and see if your graphic card is on the list.  And if it is, enable it.  Then, see if you can change the resolution to the one that you want to use.

---

### Post by Ginger Towel on 2008-03-09
yes that is enabled and i can change to the resolution i want it just gets reset (to a default?) whenever i restart or log out.

---

### Post by Ginger Towel on 2008-03-10
bump

---

### Post by Ginger Towel on 2008-03-11
anyone... please

---

### Post by dark_phantom on 2008-03-12
Have you tried nvidia-settings?  Also, what I've found better is to install envy and reinstall the nvidia drivers via envy.  Works real well and you can change settings with nvidia-settings.

sudo nvidia-settings and make sure to write to your xorg.conf to save your settings.

---

