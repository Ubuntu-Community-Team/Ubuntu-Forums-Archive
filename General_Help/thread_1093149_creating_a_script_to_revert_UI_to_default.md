---
title: "creating a script to revert UI to default"
date: 2009-03-11
forum: General Help
---

### Post by oarking on 2009-03-11
i'm going to be building a bunch of ubuntu computers for the general public. and while i'm going to be spending a few hours training each person to use it, i'd like to create my own panel organization and icon placements so as to have a kind of unified appearance.

the problem that comes to mind right away is what if someone right clicks on something and accidentally deletes that icon and doesn't know/remember how to get it back.

i'd like to create a script that all you have to do is double click on it and it will rearrange all the icons and panels into my default style without effecting any files they might have added or desktops they might have put up.

what's the best way to do this? i've got a few people on my team who can write the final product but i'd like to get some feedback so we don't end up making a 1,000 line script that could be done in 500.

---

### Post by oarking on 2009-03-13
could i make a backup of panel settings from one computer and create a script that will install them on a different computer? i don't want to change the theme or "skin" i just want the panels to be arranged and sized in a certain way with custom menus, font sizes, and icons.

---

### Post by dcstar on 2009-03-14
> **oarking said:**
> could i make a backup of panel settings from one computer and create a script that will install them on a different computer? i don't want to change the theme or "skin" i just want the panels to be arranged and sized in a certain way with custom menus, font sizes, and icons.

All those settings are in the (hidden) .gnome (and other) folders in the home directory, you should be able to simply copy over saved versions whenever anyone logs in.

---

### Post by oarking on 2009-03-15
could you identify which files do what and where they are? my .gnome folder is empty, my .gnome2 folder has all my shortcuts from one of the panels in it. but i can't find any other files that correspond to panel location, size, content, etc.

---

