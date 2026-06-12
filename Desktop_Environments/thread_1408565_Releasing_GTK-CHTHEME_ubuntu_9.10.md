---
title: "Releasing GTK-CHTHEME ubuntu 9.10"
date: 2010-02-16
forum: Desktop Environments
---

### Post by sandman3838 on 2010-02-16
Hello

I have an issue with themes at the moment.  Actually several?

First, everything was great until I went and checked out a program called GTK-CHTEME!

I didn't know it at the time but it would seem that GTK-CHTHEME doesn't like sharing with Ubuntu Appearance very well?  At the moment Appearance CONTROLS can only be changed via GTK-CHTHEME.  Even if I do a complete removal of GTK-CHTHEME it doesn't hand back use of the "CONTROL" or menu bar back to Ubuntu Appearance Controls?  

What is the default Graphic Engine and/or theme of Ubuntu 9.10 I would love to clean this up and reset it.

Finally, In my /home/username/.themes there are some 90 themes in there while in the Ubuntu Appearance Themes the are 64.  Here too I don't mind cleaning it all out and starting over.

I do have Compiz installed even though I don't ever really go into it much.

Please if there is any thing you need to be run it check on, god knows what, let me know?

Thank you for all you help.

---

### Post by stinkeye on 2010-02-16
GTK-CHTHEME writes to a hidden file in your home directory called
```
.gtkrc-2.0
```Which overrides customization set in Appearances.
ctrl + h to show hidden files.

If you delete this file, Appearances will work as before.
If you use gnome-color-chooser you will need to reapply, because this also writes to .gtkrc-2.0.

As for there being more themes in your .themes folder than in Appearances
this is because some of them aren't full themes.
ie they're just window borders or controls.

---

### Post by sandman3838 on 2010-02-22
That's what I needed to know thank you!  :)

---

