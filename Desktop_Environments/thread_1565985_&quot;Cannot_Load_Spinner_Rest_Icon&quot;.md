---
title: "&quot;Cannot Load Spinner Rest Icon&quot;"
date: 2010-09-01
forum: Desktop Environments
---

### Post by joebrueske on 2010-09-01
I had found multiple [bug reports]("https://bugzilla.gnome.org/show_bug.cgi?id=598975") about this issue. Anytime I use the Gnome-Search-Tool and attempt to search for something it crashes. In the past I just gave up, looked up the bash command for search and used the terminal command. But this time I tried running the tool from terminal to get this output:

```
** (gnome-search-tool:7878): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:7878): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:7878): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:7878): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:7878): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:7878): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:7878): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:7878): WARNING **: Cannot extract frame from the grid


** (gnome-search-tool:7878): WARNING **: Could not load spinner rest icon


(gnome-search-tool:7878): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(gnome-search-tool:7878): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gnome-search-tool:7878): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gnome-search-tool:7878): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `GDK_IS_PIXBUF (src)' failed

(gnome-search-tool:7878): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
**
ERROR:gsearchtool-spinner.c:666:bump_spinner_frame_cb: assertion failed: (frame != NULL)
Aborted
```

So, it's not finding a rest spinner animation. I looked for one in the 16x16 animation folder and there wasn't one for the theme I'm using.

What do I need to do to fix this? I've tried putting a blank 16x16 png there titled anything from process-idle to gnome-spinner-rest. I've been searching google for the past 35 minutes trying to find a solution, but haven't found one yet.

Thanks.

---

