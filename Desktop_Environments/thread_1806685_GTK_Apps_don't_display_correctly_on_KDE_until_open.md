---
title: "GTK Apps don't display correctly on KDE until opening appearance preferences"
date: 2011-07-18
forum: Desktop Environments
---

### Post by Darkness Des on 2011-07-18
I recently installed KDE and began using that instead of Unity (less buggy, IMHO) and it was running smoothly until I began configuring my GTK applications for transition in that. I installed the Oxygen-GTK them from gnome-look.org and set that as my default theme for GTK applications under the KDE appearance preferences.

When I log in, however, GTK applications just use the stock Xorg theme until I run "gnome-appearance-properties" in my terminal.

Any help with fixing this is greatly appreciated - I believe that a fix involving .gtkrc would suffice, but I honestly cannot configure it no matter how hard I try.

Thanks in advance.

---

### Post by rotave on 2011-07-18
not sure how to fix your specific problem, but i always have issues with the default GTK appearance manager in KDE. I uninstall it (kde-config-gtk) and replace it with lxappearance. so you could try that and see if it fixes your problem. however lxappearance won't show up under application appearance but will appear in your menu under settings.

---

### Post by Darkness Des on 2011-07-19
That worked perfectly, thank you VERY much!

---

