---
title: "weird XGL problem"
date: 2006-07-16
forum: Desktop Environments
---

### Post by lixx on 2006-07-16
im using KDE on my HP nx6120 laptop. the thing is, i can't change themes when im using XGL. performance is not an issue to me because XGL/Compiz works like a charm, and is very stable. in the first snapshot, the upper border doesn't change colors when i select a compiz theme, and in the second snapshot, the window tab doesn't appear in gnome-theme-manager. what can i do to fix this? i really want to customize my desktop :p

---

### Post by testube_babies on 2006-07-16
1)  If you open the "Edit" pane in the compiz-themer, you will see that the frame of a window is themed differently from the titlebar.  You can edit the theme to be the same for both if you like.

2)  The window borders tab is disabled by compiz in gnome-theme-manager because traditional metacity themes aren't supported by compiz.

---

### Post by lixx on 2006-07-16
ignore this thread :)

i've finally solved the problem. don't use gcompiz-themer0.8, instead upgrade to gcompiz-themer0.10 to resolve the issue

---

