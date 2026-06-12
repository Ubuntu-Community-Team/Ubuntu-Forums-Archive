---
title: "Panels not changing with system theme"
date: 2011-02-19
forum: Desktop Environments
---

### Post by bischofs on 2011-02-19
The panels on the desktop environment of 10.10 do not change with the theme, they are stuck on the human theme. How do I change this?

---

### Post by ve4cib on 2011-02-19
Have you double-checked that the panels are set to use the System Theme, and aren't using a fixed background colour/image?

Right-click on panel --> Properties --> Background tab

---

### Post by bischofs on 2011-02-19
Thank you but the setting is on use system theme. I Checked this first.

---

### Post by tekkidd on 2011-02-19
Try

```
killall gnome-panel
```

this should reset them to the new theme

---

### Post by bischofs on 2011-02-19
Thank you, however it is restarting the panels in the human theme still despite the theme manager being set on a different theme.

---

### Post by bischofs on 2011-02-19
I also don't have access to the Visual effects tab in the Appearance Preferences dialog box, perhaps control over the themes was set to a different application. Is there a setting for this?

---

### Post by stainless_steel on 2011-02-20
I'm in the exact same boat. The panels remain black as they were when i installed 10.10 (yesterday). theres also no options to customize the colors of anything except the text and text back ground.
Tried rebooting and killall gnome-panel
anyone got any information?

---

