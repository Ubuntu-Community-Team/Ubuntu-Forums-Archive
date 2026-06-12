---
title: "Running gnome-font-properties breaks X fonts"
date: 2006-09-07
forum: Desktop Environments
---

### Post by mo-seph on 2006-09-07
Hi all,

I've just installed Dapper on a Dell Latitude D800. I am using a non-gnome window manager (ion3) and I'm having issues with fonts as follows:

When I start the window manager, there is no problem. Programs can find fonts as necessary.

If I now start gnome-font-properties, or gnome-theme-manager etc. I get two effects:

[LIST]
[*]the font sizes in applications change (quite radically - going both to very large and very small)
[*]applications are no longer able to load fonts
[/LIST]

The test I use for the second case is running xfontsel. Run before gnome-*, it produces no output on the terminal. Afterwards, I get:

> xfontsel
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset

Other applications have problems with fonts; for example, if I reload my window manager, it cannot load any fonts for menus and titles etc.

Any ideas what's going on and how to get round it? I'd like to be able to use the gnome-themes stuff so I'm not stuck with the brutal default theme (the default ubuntu one would be fine ;) )

Thanks for any help!

---

