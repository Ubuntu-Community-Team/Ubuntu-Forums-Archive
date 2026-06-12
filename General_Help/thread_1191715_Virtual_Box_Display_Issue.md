---
title: "Virtual Box Display Issue"
date: 2009-06-19
forum: General Help
---

### Post by watsgoodg on 2009-06-19
Hey Guys,

I built a Ubuntu machine and setup VBox to automatically start and expand into full screen when the machine boots up.  The problem is the virtual machine is xp pro and when it starts up it auto adjusts but is not full screen.  Is there any ways to write a script to change the display?  Or some setting in VBox?

Thanks,
-Jason

---

### Post by lecoeus on 2009-06-19
If you always get an xp screen with black areas around it and xp is never really full screen, then it is possible that your host resolution is higher than your guest resolution. Install guest additions inside your guest xp and see if that solves the problem for you.

---

### Post by watsgoodg on 2009-06-20
thanks for the replay i have guest additions already installed i am going to check the resolution on the physical machine

---

### Post by watsgoodg on 2009-06-23
No reply's ?

---

### Post by akudewan on 2009-06-23
Install guest additions. Press Host+G to auto-resize the display. (Host is usually Right Ctrl key).

---

