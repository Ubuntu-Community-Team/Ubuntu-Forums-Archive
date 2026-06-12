---
title: "gtk2 theme editor"
date: 2011-02-27
forum: Desktop Environments
---

### Post by jester48 on 2011-02-27
Does anyone know how I can edit an individual gtk theme?  I'm loving the look of Azenis except for one small caveat.  It adds these window borders to every window...

So basically when I fullscreen my browser, there's a section on the left/right/bottom that doesn't count as inside the window...visually that's kind of annoying to me.  On top of that, sometimes my mouse will hover onto the borders and when I'm trying to scroll down with horizontal scrolling it doesn't register as "inside" the window and therefore doesn't scroll.

I know this is a theme issue, because if I change the theme back to "Ambience" then the borders are gone, but I'm a little attached to the look of Azenis.

Thanks for any help

---

### Post by Krytarik on 2011-02-27
I just yet installed the theme to check it, and I don't notice a different behaviour of fullscreened Firefox (what browser do you use?) than with the Ambiance theme. Generally there is no window decoration (borders/titlebar) at all of fullscreened windows. Could you provide a screenshot?

---

### Post by jester48 on 2011-02-27
Oops, I didn't mean fullscreen...I meant maximized...my bad.

Here's a screenshot anyways.  I'd like to be able to remove those borders if at all possible.

Thanks

---

### Post by Simian Man on 2011-02-27
That's controlled by the Metacity theme, not the GTK+ theme.

If you go to where you have the theme installed, then open the file "metacity-1/metacity-theme-1.xml" you can edit the theme with a text editor.  Decreasing the widths in the frame geometry section should do what you want.

---

### Post by Krytarik on 2011-02-27
Do you use the Metacity window decoration (default) or those for Emerald?

Metacity: Open the file "metacity-theme-1.xml" in the "metacity-1" subdirectory of the theme. Change the window geometrics in the upper part of the file.

Emerald: Open "System -> Preferences -> Emerald Theme Manager, click the tab "Edit Themes", then at "Frame/Shadows". Change the values at the right side.

EDIT: I don't know if Emerald works in the Netbook Edition.

---

### Post by jester48 on 2011-02-27
A-HA!

You guys are awesome...now off to figure out how to mark this as SOLVED.

Thanks again :)

---

