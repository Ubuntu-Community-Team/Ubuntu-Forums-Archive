---
title: "Local $HOME/.gtkrc location changed to $HOME/.gtkrc-1.2-gnome2 in Jaunty"
date: 2009-10-14
forum: Desktop Environments
---

### Post by OrangeVixen on 2009-10-14
After much hacking, I figured it out, as of Ubuntu 9.04, the local GtkRcFile location has changed from ~/.gtkrc to ~/.gtkrc-1.2-gnome2

If you are just coping over or keeping an old .gtkrc from a prior version, it won't get read and you need to rename it to .gtkrc-1.2-gnome2.

You can also set the environment variable GTK_RC_FILES, like this:

GTK_RC_FILES=/etc/gtk/gtkrc:/home/user/.gtkrc

But I'd recommend renaming it to .gtkrc-1.2-gnome2 to adapt to the new standard.

Note that this is for GTK, not GTK-2 (a totally different thing).

---

