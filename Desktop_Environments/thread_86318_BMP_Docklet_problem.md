---
title: "BMP Docklet problem"
date: 2005-11-04
forum: Desktop Environments
---

### Post by Zhukov on 2005-11-04
Hi there!
Im having a small problem with the bmp docklet...
When i click on the bmp icon at the dock, bmp closes!! :S Any suggestion?

---

### Post by bionnaki on 2005-11-04
yeah, I use bmp & the docket...I played around with it. the docket will work only if the playlist is the same width as the actual player. its a bug with the docket that hasnt been fixed.

---

### Post by bionnaki on 2005-11-04
oh...and if you turn off the visualization in bmp, you can have the playlist any size & have the docket work. I hope the docket developer fixes these bugs, bmp is a great player.

---

### Post by bionnaki on 2005-11-04
there's a patch availabe that supposed will correct this
[http://mark.xnull.de/forums/viewtopic.php?id=17](http://mark.xnull.de/forums/viewtopic.php?id=17)

> --- beep/vis.c.orig     2004-12-04 10:04:29.000000000 +0100
+++ beep/vis.c  2005-02-17 12:02:25.391044008 +0100
@@ -223,7 +223,8 @@ vis_draw(Widget * w)
     /* FIXME: The check "shouldn't" be neccessary? */
     /* if (GTK_IS_WINDOW(vis->vs_window)) { */
     GDK_THREADS_ENTER();
-    gdk_draw_indexed_image(vis->vs_window, vis->vs_widget.gc,
+    if (GDK_IS_DRAWABLE(vis->vs_window))
+        gdk_draw_indexed_image(vis->vs_window, vis->vs_widget.gc,
                            vis->vs_widget.x, vis->vs_widget.y,
                            vis->vs_widget.width, vis->vs_widget.height,
                            GDK_RGB_DITHER_NORMAL, (guchar *) rgb_data,



how/where I apply this, I have no idea.

---

### Post by Zhukov on 2005-11-06
Turn off visualisation? What visualization? Mine is off, and still i get an error, but fixing the widht of the playlist worked :D thanks

---

