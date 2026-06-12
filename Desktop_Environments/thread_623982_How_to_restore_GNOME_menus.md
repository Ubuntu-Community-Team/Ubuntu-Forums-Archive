---
title: "How to restore GNOME menus?"
date: 2007-11-26
forum: Desktop Environments
---

### Post by ichudov on 2007-11-26
I installed Ubuntu to coexist with my Fedora. 

What I want is to FULLY UNSET my Gnome configuration and make sure that I have blank, virginal, completely stock Gnome menu that is compatible with Ubuntu. Right now I have a mess, menu is missing, etc. 

That is, I do not want any holdovers from the past times of Fedora -- I want to restore a clean slate. 

I am pretty good with command line and would prefer a CLI solution.

Thanks

---

### Post by gamma on 2007-11-26
> **ichudov said:**
> I installed Ubuntu to coexist with my Fedora. 

What I want is to FULLY UNSET my Gnome configuration and make sure that I have blank, virginal, completely stock Gnome menu that is compatible with Ubuntu. Right now I have a mess, menu is missing, etc. 

That is, I do not want any holdovers from the past times of Fedora -- I want to restore a clean slate. 

I am pretty good with command line and would prefer a CLI solution.

Thanks

The menu data is in ~/.config/menus/*
I usually clear those files out to reset my menu.

(You'll have to log out and log back in to see the changes)

---

