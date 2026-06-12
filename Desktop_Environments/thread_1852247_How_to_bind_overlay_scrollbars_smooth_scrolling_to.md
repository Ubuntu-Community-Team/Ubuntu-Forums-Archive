---
title: "How to bind overlay scrollbars smooth scrolling to mouse wheel?"
date: 2011-09-29
forum: Desktop Environments
---

### Post by hiperion85 on 2011-09-29
Hello everyone,

I've tested the second Oneriric Ocelot Beta and I've noticed that they have simulated a smooth scrolling effect when clicking on the steppers of the overlay scrollbar.

I've been wondering if there is some way to bind the mouse wheel up and down actions to the actions of the overlay scrollbar steppers. Maybe through the input configuration files?

What do you think?

---

### Post by hiperion85 on 2011-09-30
Nobody?

---

### Post by Copper Bezel on 2011-09-30
The methods used are different. The up and down step for scrolling from the mouse wheel or trackpad is defined in the X server, while scrolling within a window is controlled by the application. I don't think there's any way to bind one to the other (and even if it could be done, it would have unfortunate results, like breaking the use of the mouse scrolling for other features, such as zoom and non-scrollbar range controls.)

---

