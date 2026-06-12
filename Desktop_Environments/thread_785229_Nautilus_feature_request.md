---
title: "Nautilus feature request"
date: 2008-05-07
forum: Desktop Environments
---

### Post by Jetze on 2008-05-07
Very simple: allow the size column to display the exact file size, so not rounded to Kb or MB.

---

### Post by DaVince21 on 2008-05-07
Isn't this rather something you should discuss on the official Nautilus page, rather than here?

[http://www.gnome.org/projects/nautilus/](http://www.gnome.org/projects/nautilus/)

There doesn't seem to be a forum, but I can see some contact info and a mailing list in the bottom right corner.

---

### Post by Awalton on 2008-05-07
Index: libnautilus-private/nautilus-file.c
===================================================================
--- libnautilus-private/nautilus-file.c	(revision 14143)
+++ libnautilus-private/nautilus-file.c	(working copy)
@@ -5000,7 +5000,8 @@
 	if (file->details->size == -1) {
 		return NULL;
 	}
-	return g_format_size_for_display (file->details->size);
+	/* hack for Jetze on Ubuntu forums */
+	return g_strdup_printf ("%"G_GUINT64_FORMAT, (guint64)file->details->size);
 }

Grab the source, patch p0 < that_patch.diff, ./autogen && make && sudo make install, enjoy.

---

### Post by Jetze on 2008-05-08
Excellent! If I feel bold and adventurous one fine day, I'll try it.

---

