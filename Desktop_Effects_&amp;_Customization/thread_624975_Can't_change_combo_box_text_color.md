---
title: "Can't change combo box text color"
date: 2007-11-27
forum: Desktop Effects &amp; Customization
---

### Post by Mohonri on 2007-11-27
I recently installed the Darker Theme under Gutsy, and I've been playing around with the gtkrc file to tweak it just the way I like it.  I'm almost there, but there's one thing I haven't been able to do:  change the text color of a combo box.

I can change the color of the combo box text before I click it--both NORMAL and PRELIGHT.  However, the text that appears in the list when I click on the combo box does not seem to follow any of the rules I've set up.  To test whether what I'm doing is having any effect, I'm using the "View as Icons/View as List" button in nautilus (file browser).

I'm pretty new to GTK, so I'm a bit mystified.  I spent a bunch of time trying to figure out what GTK widget (or whatever) needs the change.  I've hit everything from GtkComboBox to GtkCellRendererText, with no luck.  Are there any GTK gurus here that can help me out?  I've attached the gtkrc file, along with the panel.rc that gets included at the end and the .gtkrc-2.0 in my home directory.

---

