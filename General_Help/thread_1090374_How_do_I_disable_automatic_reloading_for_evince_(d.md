---
title: "How do I disable automatic reloading for evince (document viewer)?"
date: 2009-03-08
forum: General Help
---

### Post by rrwo on 2009-03-08
I am writing articles using LaTeX, and whenever I rebuild a PDF, evince (the document viewer) automatically reloads the document.  This is a problem, because the command-line window often fills with a lot of complaints from evince, which obscures the error message.

How do I disable reloading? I cannot find a preferences menu in evince.

---

### Post by Dennis Benzinger on 2009-03-26
This automatic reloading annoys me too.

FWIW, I've filed a feature request on the Evince bug tracker:
[http://bugzilla.gnome.org/show_bug.cgi?id=576855](http://bugzilla.gnome.org/show_bug.cgi?id=576855)

---

### Post by rrwo on 2009-09-06
There's no way to disable it, at least in the current version of Evince. You have to manually patch it yourself, using this patch (supplied to me by Evince maintainers):
```

Index: shell/ev-window.c
===================================================================
--- shell/ev-window.c	(revision 3553)
+++ shell/ev-window.c	(working copy)
@@ -1276,7 +1276,7 @@
 ev_window_document_changed (EvWindow *ev_window,
 			    gpointer  user_data)
 {
-	ev_window_reload_document (ev_window);
+	// ev_window_reload_document (ev_window);
 }
 
 static void

```

---

