---
title: "beryl makes my minimize / resize / close windows option dissapear"
date: 2007-06-18
forum: Desktop Effects &amp; Customization
---

### Post by dronepower on 2007-06-18
Beryl makes the minmize / resize / close windows box options dissapear.

I did run Beryl nicely yesterday. The only thing I changed was under the nvidia options in twinview make the monitors settings change to position " absolute".

Does anyone know how to solve this problem?

---

### Post by bergersau on 2007-06-18
I had a similar problem.

Solved it by selecting a different window manager by right clicking on the 'Emerald' theme manager icon if I remeber rightly.

Was a couple of months ago so I can't remember any more details. Hope this helps.

---

### Post by dronepower on 2007-06-22
My problem was solved using follwing command in terminal:

sudo nvidia-xconfig --add-argb-glx-visuals

---

### Post by Karl S. on 2007-06-22
Is this safe with an ATI card?

---

### Post by pardesi on 2007-06-22
> **Karl S. said:**
> Is this safe with an ATI card?

manually add this line
```
Option      "AddARGBGLXVisuals" "True"
```
 below the driver name in the device section of 
```
sudo gedit /etc/X11/xorg.conf
```

---

