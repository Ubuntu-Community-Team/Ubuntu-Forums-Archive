---
title: "Howto reset color profile"
date: 2012-01-27
forum: Desktop Environments
---

### Post by engineer on 2012-01-27
How can I reset my color profile for GTK or Gnome apps?

In particular the problem is:
I installed the same theme on two machines, where in one case I get white font on a dark gray unity panel, which is fine to read, but on the other machine this font is black and therefore unreadable.

I remember that I played with these settings with the old Gtk Theme Manger, which is now changed as of Ubuntu 12.04 (?). I wonder if there is a way to reset this to factory defaults.

I'm running Oneiric with the stock version of unity, in case that matters.

---

### Post by Krytarik on 2012-01-27
> **engineer said:**
> How can I reset my color profile for GTK or Gnome apps?
[..]
I'm running Oneiric with the stock version of unity, in case that matters.
I've just googled that, and it seems like for GTK+ 3, this file is used to override any other GTK+ settings, check that: "~/.config/gtk-3.0/gtk.css".

Hope this helps.

---

### Post by engineer on 2012-01-27
I don't have that file. Obviously because I didn't override any gtk-3 settings yet. I guess I need to change leftover gtk-2 settings.

What I found so far is that these settings could be stored in ~/.gtkrc-2.0. I have that file but it's empty. Where else could these settings be?

---

### Post by Krytarik on 2012-01-27
> **engineer said:**
> I don't have that file. Obviously because I didn't override any gtk-3 settings yet. I guess I need to change leftover gtk-2 settings.

What I found so far is that these settings could be stored in ~/.gtkrc-2.0. I have that file but it's empty. Where else could these settings be?
Actually, old GTK+ 2 settings shouldn't affect GTK+ 3, but yes, this would be file containing the general GTK+ 2 overrides. And if you have a theme with custom settings under "~/.themes" in your home directory, it would override the settings of those possibly installed system-wide. So I'd definitely check that, too.

Btw., what do you mean with "Gtk Theme Manager", maybe "Gnome Color Chooser"?
If yes, at the first glance it seems like it only affects the "~/.gtkrc-2.0" and "~/.themes".

---

### Post by engineer on 2012-01-28
I was referring to the old gnome theme manager, where you could set gtk and window manager theme and colors as well. This page disappeared with the change to gtk-3, if I remember correctly. My guess was that from changing the color settings there, I could have some leftover color settings.

I'm still lost, I tried to modify the .css files in my theme directory. Nothing seemed to affect the font color in the unity panel. I always changed themes back and forth to reload the settings. And I downloaded a newer version of the theme and installed it, which should overwrite all files in that directory, but also that didn't help. The text in the panel is still rendered somewhat lighter gray on dark gray.

---

### Post by Krytarik on 2012-01-28
> **engineer said:**
> I was referring to the old gnome theme manager, where you could set gtk and window manager theme and colors as well. ... My guess was that from changing the color settings there, I could have some leftover color settings.
Try this, even though it would be quite weird if it would actually work, for multiple reasons :P :
```
gconftool-2 --unset /desktop/gnome/interface/gtk_color_scheme
```

---

### Post by engineer on 2012-01-30
As expected, that didn't change things.

---

