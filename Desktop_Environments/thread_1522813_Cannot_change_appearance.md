---
title: "Cannot change appearance"
date: 2010-07-02
forum: Desktop Environments
---

### Post by nuncio.bitis on 2010-07-02
Recently Ubuntu on my computer upgraded itself to 10.04
Since then, I cannot change the appearance without rebooting.
Preferences -> Appearance
Every time I choose a theme, the cursor bounces to the top of the window, and selects a new theme called "Custom"  It almost looks like the theme I selected, but not quite.  Then I can choose the theme I previously clicked on.
There really should be an "Apply" button.  I don't think it was a good idea to change things so you have to reboot for an appearance to take effect.  The previous version of Ubuntu used to do this.  Also - the preferences window shows the Minimize/Maximize/Close buttons on the top right of windows, however after I reboot they switched to the top left.  Is there a way to choose this instead of being forced to be the opposite of what I expect?

---

### Post by _Mark_ on 2010-07-02
You shouldn't need to reboot, the theme should change  when selected

What I would suggest is run > gnome-appearance-properties in a terminal, you should see any errors,if any in the terminal window when you change the theme, this may help in diagnosing the problem

---

### Post by nuncio.bitis on 2010-07-02
Just these errors on startup:

(gnome-appearance-properties:11163): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:11163): Gdk-CRITICAL **: gdk_display_sync: assertion `GDK_IS_DISPLAY (display)' failed

(gnome-appearance-properties:11163): Gtk-CRITICAL **: gtk_tree_model_sort_real_unref_node: assertion `elt->ref_count > 0' failed

---

### Post by nuncio.bitis on 2010-07-06
> **_Mark_ said:**
> You shouldn't need to reboot, the theme should change  when selected

What I would suggest is run  in a terminal, you should see any errors,if any in the terminal window when you change the theme, this may help in diagnosing the problem


That's what I'm saying.  I shouldn't need to reboot just to change the theme.  Is there any way of changing things so I don't have to?  Is there a new version due out to change this?
Thanks!

---

### Post by yossell on 2010-07-06
I think _Mark_ was saying that, for the rest of us, the appearance changes the moment a new theme is selected, i./e without a logout or reboot or anything. So it's not a problem with the version.

I can tell you that, on my system, theme changes immediately, however, just like you, I get the first two Gdk-critical  errors that you do, so this doesn't look like the problem. The error I don't get is your third one, the one about the tree, so this may be the source of the problem.

---

### Post by nuncio.bitis on 2010-07-10
> **yossell said:**
> I think _Mark_ was saying that, for the rest of us, the appearance changes the moment a new theme is selected, i./e without a logout or reboot or anything. So it's not a problem with the version.

I can tell you that, on my system, theme changes immediately, however, just like you, I get the first two Gdk-critical  errors that you do, so this doesn't look like the problem. The error I don't get is your third one, the one about the tree, so this may be the source of the problem.


I think I found the problem.  I deleted the .themes directory from my home directory, and now I can switch themes (using the remaining default themes).  I'll just have to re-download and reinstall the themes I want.  At least it's working again.

---

