---
title: "How to find GTK Widget Names?"
date: 2007-11-08
forum: Desktop Effects &amp; Customization
---

### Post by bathtoy on 2007-11-08
I am customizing a gtk-2.0 theme file.
Because my theme does not work perfectly for all applications I have to write the odd "fix" where I change the style for an individual application.

For example, here is one that works perfectly for Banshee: 

[FONT="Courier New"]
# Banshee fix
widget "*Banshee*"           style "alternate-colors"
[/FONT]

However, when I try to create a fix for Filezilla I cannot get it to work:

[FONT="Courier New"]
# FileZilla fix
widget "*Filezilla*"         style "alternate-colors"
[/FONT]

It seems I have **guessed** the wrong widget name (*Filezilla*). Please tell me how I find the correct name? I have the same problem with Acroread.

---

