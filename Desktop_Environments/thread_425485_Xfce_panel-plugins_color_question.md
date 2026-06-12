---
title: "Xfce panel-plugins color question"
date: 2007-04-27
forum: Desktop Environments
---

### Post by skep on 2007-04-27
Hi!

System: xubuntu 7.04

Problem: I have some xfce-panel-pluins like systemload-plugin, networkmonitor ect. and in each of them you can define a color for the bars, but i can't change them..they always appear in blue, no matter what I set.

Why is that?

---

### Post by skep on 2007-04-27
problem fixed by using another gtk2-theme..

---

### Post by x1a4 on 2007-04-27
Hi,

The panel plug-ins use the progress bar widget.  Some GTK themes (Clearlooks for example) use an image for it's progress bars which overrides any colour settings.  That's why when you changed UI settings you saw the colours in the plug-ins.

---

