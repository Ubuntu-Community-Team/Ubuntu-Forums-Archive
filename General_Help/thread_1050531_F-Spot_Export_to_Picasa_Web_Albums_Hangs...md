---
title: "F-Spot Export to Picasa Web Albums Hangs.."
date: 2009-01-25
forum: General Help
---

### Post by ellemenope on 2009-01-25
I've been having a persistent and annoying problem when trying to export photos to Picasa from F-Spot. It only started happening recently, but almost everytime I try to export photos, it will upload on or two (or none at all) and then hang.

Running from the terminal, I've found this:
> (firefox:23308): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(firefox:23308): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

I have it set-up so photos are resized before upload, I'm guessing these errors have to do with that. Is it a problem with F-spot or Firefox? Is there anything I can do to fix it? Its not as though I can't upload photos, it just takes about 5 tries to get a batch of about 15 up...

---

### Post by trispad on 2009-01-27
Did you ever find a solution to this problem?  I seem to be having the same issue.

trispad

---

### Post by ellemenope on 2009-01-28
Nope, still hangs frequently.

Update:

I might have found a fix, try testing this hypothesis: Don't have firefox open whilst uploading photos.

---

