---
title: "Customising Gtk icons outside GNOME."
date: 2006-01-09
forum: Desktop Environments
---

### Post by kyku on 2006-01-09
Hi I'd like to use some non-default icon sets I found on [http://gnome-look.org](http://gnome-look.org) . How does one turn them on without any GUI configurator ?

---

### Post by kyku on 2006-01-10
Ok, I figured it out on my own. This is how it looks like:

1) download icon theme archive.
2) unpack the archive to ~/.icons.
3) edit ~/.gtkrc-2.0, add a line saying
```
gtk-icon-theme-name="subdirectory-name-in-icons"
```

That should do the trick.

---

