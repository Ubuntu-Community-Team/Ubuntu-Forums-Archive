---
title: "How to create a theme (?)"
date: 2008-04-10
forum: Desktop Effects &amp; Customization
---

### Post by byrd on 2008-04-10
Okay, so after *months* of looking through gnome-look and elsewhere and not quite being able to find a theme I really like I thought I may as well use my design skills and create my own.. but where do I start?

I'm not sure what to look for, actually, is it GDM, GTK, Metacity, etc? Preferably as less code as possible but I do have some experience. Also, since I'll be creating a mockup in Photoshop, is there a recommended size to start at? What I mean is, my resolution is 1440x900 but I'd want my theme to be used on whatever resolution without being 'low quality.'

Edit: To clarify, I'm just looking to make a general theme for Gnome, so one that would control colours, window borders, the min/max/close buttons, etc.

---

### Post by tedt on 2008-04-10
you are asking a broad question -

there are lots of different elements you want to theme.  The best place to start is with GTK which is the GIMP Tool Kit or the code that controls the general look and feel of GNOME.  You might want try to modify an existing theme using a combination of various gtk engines.

Window Border is control by Metacity for a standard gnome, if you are using compiz then you may be using emerald 
Color is controlled through the GTK theme, as are the widgets (check boxes, scroll bars, buttons, etc)

---

