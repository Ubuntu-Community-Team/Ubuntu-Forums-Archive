---
title: "Top gnome panel wierdness.."
date: 2007-03-23
forum: Desktop Environments
---

### Post by eitan_a on 2007-03-23
Hey guys..

I am trying to use a background for my top gnome panel.  It is attached.  When I replace my theme's top panel panel-bg.png with this one in .themes, it comes out looking like attached.  What is going on? 
Thanks!

---

### Post by mcduck on 2007-03-24
Do you mean that you are trying to use that image bin a GTK theme? I don't think you can do that with other than tileable images. Instead you could use it as the panel background through Gnome Panel's own options..

---

### Post by eitan_a on 2007-03-24
I fixed it.  You need to comment out the panel-bg.png lines in the gtkrc file and then use the background file by right-clicking the panel.  Otherwise it didn't work for me.

---

