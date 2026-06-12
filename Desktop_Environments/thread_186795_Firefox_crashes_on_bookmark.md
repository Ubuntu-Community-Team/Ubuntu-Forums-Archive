---
title: "Firefox crashes on bookmark"
date: 2006-06-02
forum: Desktop Environments
---

### Post by edwina on 2006-06-02
I have clean-installed Kubuntu Dapper, but Firefox crashes on me whenever I go to "Bookmark this page". I've installed the Firefox debug package, but don't know where to find the debug info. Can anybody help me out with this one?

Thanks.

---

### Post by Rackerz on 2006-06-02
Run FireFox from the Terminal try to bookmark a page and when it crashes an error should come up in the Terminal.

---

### Post by edwina on 2006-06-02
That worked for getting the debug info, thanks.

Terminal gives the following, which I hope means something to you all ...
```

(Gecko:5184): Gtk-CRITICAL **: gtk_widget_get_parent_window: assertion `GTK_IS_WIDGET (widget)' fail                                         ed

(Gecko:5184): Gdk-CRITICAL **: gdk_pixbuf_get_from_drawable: assertion `src != NULL' failed

(Gecko:5184): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_n_channels: assertion `pixbuf != NULL' failed

(Gecko:5184): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' fail                                         ed

(Gecko:5184): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(Gecko:5184): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(Gecko:5184): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(Gecko:5184): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(Gecko:5184): Gtk-CRITICAL **: gtk_widget_get_parent: assertion `GTK_IS_WIDGET (widget)' failed
Segmentation fault
```

---

### Post by aysiu on 2006-06-02
[It's not looking good for you](http://www.google.com/search?num=100&hl=en&lr=lang_en&safe=off&q=Gtk-CRITICAL+**%3A+gtk_widget_get_parent_window%3A+assertion+%60GTK_IS_WIDGET+%28widget%29%27+fail&btnG=Search).

You wouldn't happen to have the wrong architecture package, would you? Say, an i386 Firefox on an AMD64 Kubuntu installation?

Are you using a Ubuntu Firefox or a Mozilla Firefox? Or some variant like Swiftfox, Flock, or Bon Echo?

---

### Post by edwina on 2006-06-02
Ah, aysiu, reminding me to use Google was all that it took in the end!

Some other person had a gtk widget error, and was advised to delete their /home/username/.mozilla directory. I tried it, and it worked. Hurrah!

Thanks for your help.

---

