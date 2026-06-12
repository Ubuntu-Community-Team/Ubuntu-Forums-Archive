---
title: "[SOLVED] Desktop Effects in Gutsy"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by JawsThemeSwimming428 on 2007-10-20
I just tried to enable Desktop Effects in a fresh install of Gutsy by going to System -> Preferences -> Appearance and using the Visual Effects tab. I have an nVidia GeForce 7300GT graphics card and I get the following error when I select to enabled the nVidia driver for the desktop effects: 

The software source for the package

   nvidia-glx-new

 is not enabled.

How do I enable them? I tried using Synaptic to install the driver but it won't let me.

---

### Post by Kimmik on 2007-10-20
Go to synaptic > preferences > sources  and enable "proprietary drivers (restricted)".
Reload and install nvidia-glx-new

---

### Post by JawsThemeSwimming428 on 2007-10-21
When I did that, I restarted X, and it restarted in low graphics mode. What am I missing?

---

### Post by JawsThemeSwimming428 on 2007-10-21
I still am not able to enable desktop effects in Gutsy. Whenever I try to I restart X and it restarts in low graphics mode. What am I doing wrong?

---

### Post by ruibernardo on 2007-10-21
If you have the driver installed, just enable it in the menu System, Administration, Restricted drivers manager. Then restart.

---

