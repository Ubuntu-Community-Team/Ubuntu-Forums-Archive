---
title: "Change color of panel clock font in Gnome"
date: 2007-01-20
forum: Desktop Environments
---

### Post by randiroo76073 on 2007-01-20
How can I change the color of the font in the gnome panel clock?

---

### Post by mcduck on 2007-01-20
Create a file called .gtkrc-2.0 inside your home directory and paste the following code into it:

```
style "panel-clock"
{
  fg[NORMAL] = "#000000"
}
widget "*.clock-applet-button.*" style "panel-clock"
```
(Change the #000000 to whatever color you want.) Then save the file, log out and back again.

---

### Post by randiroo76073 on 2007-01-20
Thanks mcduck, have a good one :)

---

### Post by randiroo76073 on 2007-01-20
Any other ideas, that didn't work at all.  Restarted & rebooted both, no change.

---

### Post by zelluloidtraum on 2007-01-23
> **randiroo76073 said:**
> Any other ideas, that didn't work at all.  Restarted & rebooted both, no change.

Worked for me in Edgy. Did you get the part about changing "000000" to whatever color you want?

---

### Post by executor on 2007-01-24
Thanks :)  worked for me to in Edgy. the clock is white now.

---

### Post by randiroo76073 on 2007-01-24
Yup, changed mine to white[#FFFFFF] & it's still black after many reboots.

---

### Post by spydon on 2008-05-19
Awesum, it amazing how much you can tweak gnome! :guitar:

---

