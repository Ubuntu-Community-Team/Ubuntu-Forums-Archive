---
title: "How to make the dash (launcher) dodge (intelligently auto-hide) again"
date: 2012-06-19
forum: Desktop Environments
---

### Post by Gannin on 2012-06-19
Apologies if this small tutorial has already been posted by someone else.

This is in regards to Ubuntu 12.04.  I'm using this in Unity 2D, so I'm not sure if this can be adapted to regular Unity.  Perhaps someone can comment on this.

I know there are a variety of programs out there meant to re-enable the dodge feature of the dash in Ubuntu 12.04, but I've heard some complain that they're buggy, and besides, they're really unnecessary.

To restore the dodge feature, first install the package "dconf-tools" using whatever installation method you prefer.

After installing that package, run either "dconf-editor" from a terminal, or bring up your application search window and type in "dconf".

In the window that pops up, go to com > canonical > unity-2d > launcher.

Find the line that says "hide-mode", double-click on its value, change the value to "2", and hit enter.  This should restore the old dodge behavior of the dash.

---

