---
title: "Font size in Xubuntu"
date: 2006-07-30
forum: Desktop Environments
---

### Post by robek on 2006-07-30
I have slight problem with the font size in Xubuntu
It's setup to Sans 9 in User Interface Prefs but it apears to be different in Applications Menu and some apps
It looks all right in i.e. Firefox, User Interface Prefs etc. but in the main menu and i.e Synaptic its much smaller

when I change the size in Preferences fonts change but the size difference remains...

When I login as a different user - root-  it all looks all right

How can I fix that?

robek

---

### Post by robek on 2006-08-01
Solved!
problem is that when you change font size in user preferences it doesn't save dpi with it
solution is to edit:
~/.config/xfce4/Xft.xrdb
and add following line somewhere at the end:
Xft.dpi: 96

---

### Post by SynapseKDE on 2008-01-01
Thanks! I was having the same problem.

---

