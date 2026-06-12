---
title: "GDM not redrawing desktop an kittens?"
date: 2011-02-02
forum: Desktop Environments
---

### Post by corkymoo on 2011-02-02
No problem with kittens.  I am using Ubuntu 10.04 LTS Lucid Lynx.  I have kept up with updates. Checked with gconf-editor that all visibility is checked.  This does not happen all the time but frequently.  Some times files created in Desktop the icons will not be created and when they are created and you delete the file the icons are not deleted.  Rebooting or restarting GDM fixes the icons.    

Thanks to all who have worked on this marvelous OS!

---

### Post by Copper Bezel on 2011-02-02
Double post, sorry.

---

### Post by Copper Bezel on 2011-02-02
Weird. I've noticed that the desktop view doesn't always refresh until it gets focus, either by minimizing everything or by clicking on it, and I've gone as far as to open the Desktop folder in a Nautilus window to check that things were there, until I figured it out. Of course the desktop is just one big Nautilus pane....

Is it possible that Nautilus is hanging? Try 

killall nautilus

next time to restart Nautilus and see if it refreshes the kittens.

---

