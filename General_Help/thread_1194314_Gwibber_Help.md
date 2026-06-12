---
title: "Gwibber Help"
date: 2009-06-22
forum: General Help
---

### Post by tmj42488 on 2009-06-22
I installed Gwibber for Ubuntu via Synaptic and quickly found some themes to better fit my GTK. The only problem is that when I go to select an theme in the preferences, there is no little drop down menu, like there should be. There is a heading, but nothing else. I'll attach a screenshot to better explain.

Anyone have any clue what might be causing this?

---

### Post by Patriciologico on 2009-06-25
1.- ```
sudo aptitude purge gwibber
```

2.- remove folder /home/user/.gconf/apps/gwibber

3.- ```
sudo aptitude install gwibber
``` from canonical repository (default)

---

