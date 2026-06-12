---
title: "Gtk-warning and segmentation fault in shares-admin"
date: 2008-12-02
forum: Desktop Environments
---

### Post by haloedrain on 2008-12-02
I'm trying to remove shared folders using the samba shared folders tool following the instructions here: [https://help.ubuntu.com/8.10/internet/C/networking-shares.html](https://help.ubuntu.com/8.10/internet/C/networking-shares.html)

I go to the terminal, type shares-admin, and get "Gtk-WARNING **: Unknown property: GtkComboBox.items"  The window attempts to load anyway, but before anything but the frame loads there's a segmentation fault and it closes.

Running the command with sudo does exactly the same thing, except the drive works a lot harder first and the Gtk-WARNING comes with a second "CRITICAL **: Unable to lookup session information for process '26609'"

Is there another way to remove shared folders?  Is this the same tool that used to be accessed from the menu like in these instructions: [https://help.ubuntu.com/7.10/internet/C/networking-shares.html](https://help.ubuntu.com/7.10/internet/C/networking-shares.html)
(And why did the handy menu item go away, anyway?)

---

