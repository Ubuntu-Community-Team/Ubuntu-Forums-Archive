---
title: "[SOLVED] compiz-fusion toolbar not displaying"
date: 2007-10-07
forum: Desktop Effects &amp; Customization
---

### Post by RyanZec on 2007-10-07
my top bar for all apps(like for firefox, the bar that says the app name "FireFox and have the min/max/close button don't display when i enable compiz by doing atl+f2 and type "compiz"  I followed this [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) but it still does appear( i have gtk-window-decorator next to command in the window decorator plugin.  am i missing another else?

---

### Post by Forlong on 2007-10-07
What type of graphics card are you using?

---

### Post by RyanZec on 2007-10-07
AGP NVidia GeForce 7600 512MB

---

### Post by Forlong on 2007-10-07
Have a look at what I wrote in the Troubleshooting section for Nvidia users.

---

### Post by RyanZec on 2007-10-07
i do have the restricted driver running and installed nvidia-glx-new and still getting no top toolbar.  is thier a wya to disbale compiz wiothout restart the x server(ctrl-alt-backspace)

---

### Post by Forlong on 2007-10-07
I was talking about the command for the terminal. Did you try that?
(you have to restart X so it can take effect)

You can disable Compiz by running
```
metacity --replace
```

---

### Post by RyanZec on 2007-10-07
yup that fixed it.

BTW how can i mark a thread as [SOLVED](i think that is possible because i have seen that)?

---

### Post by Forlong on 2007-10-08
Thread Tools &#8594; Mark this thread as solved

---

