---
title: "Beryl Problem"
date: 2007-08-22
forum: Desktop Environments
---

### Post by nx0 on 2007-08-22
I recently installed Ubuntu Feisty Fawn to dual-boot with Vista.

I had no problems with it up until I tried using Beryl. Beryl seems to somewhat work, the cube works fine. The only problem is I can't move windows, and windows don't have the minimize, maximize and close buttons.

I've tried tons of solutions for this.

I'm using an NVIDIA GeForce 6150 LE graphics card, so I installed the legacy drivers for that. I've tried running
```
sudo nvidia-xconfig --add-argb-glx-visuals
```
then logging out and back in, but still no luck. I've tried re-installing Beryl several times even after that, and still no luck.

Is there any way to fix this? Or will I just not be able to run Beryl?

---

### Post by nx0 on 2007-08-22
Anyone?

---

### Post by Clay_Banger on 2007-08-22
do you have beryl-manager installed?
and do you have emerald and emerald-themes installed?

---

### Post by nx0 on 2007-08-22
Yeah, I've installed both. Emerald theme is on and so is the manager, but the problem still persists.

---

### Post by tekkenlord on 2007-08-22
Check the xorg.conf file to see if you are running in default depth 24. If not, change it to 24. Also, you must go to the beryl-manager settings and make sure you have activated the "Move window" option. Hope it helps!

---

