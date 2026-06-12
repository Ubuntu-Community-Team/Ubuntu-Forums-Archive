---
title: "Gaia Nova and Elegant Brit Help"
date: 2008-12-10
forum: General Help
---

### Post by Plantmiester on 2008-12-10
Two themes using GTK+ engines.  Two themes producing the same error message:

"This theme will not look as intended because the required GTK+ theme engine '' is not installed."

There is no engine listed.  And I am at a loss as to what engine, whether it's in the repositories or not, not install for these two themes.

[Gaia Nova at GNOME-Look]("http://gnome-look.org/content/show.php?content=75930&forumpage=0")

[Elegant Brit at GNOME-Look]("http://gnome-look.org/content/show.php?content=74553&forumpage=19")

I'm on Ubuntu 8.10, with most of the theme engines in the repository installed.

---

### Post by urukrama on 2008-12-10
You'll need the pixmap engine. I believe it is now part of the [gtk2-engines-pixbuf]("http://packages.ubuntu.com/intrepid/graphics/gtk2-engines-pixbuf") package.

---

### Post by Ivo Moelans on 2008-12-10
You can find the answer here: [http://ubuntuforums.org/showpost.php?p=6148824&postcount=14]("http://ubuntuforums.org/showpost.php?p=6148824&postcount=14")

---

### Post by Plantmiester on 2008-12-15
It helped clear up installation issues in Gaia, but a significant number of features aren't showing up, such as custom applications menu logo, and the top bars of windows.

In Elegant Brit no change occurs, in fact the gtkrc file doesn't even have the entry "unstyle" in it, so the fix doesn't work.  This style still misses key features (such as the flattening of title bars and a large number of missing colours.

---

### Post by Ivo Moelans on 2008-12-15
> In Elegant Brit no change occurs, in fact the gtkrc file doesn't even have the entry "unstyle" in it, so the fix doesn't work.

Elegant Brit **does** have a style "unstyle". You overlooked it: it is on lines 1727 to 1731 and if you apply the fix it does work.

As for your new questions: what do you mean by *title bars* and *missing colors*?

> It helped clear up installation issues in Gaia, but a significant number of features aren't showing up, such as custom applications menu logo, and the top bars of windows.

The author seems to have provided a *start-here.png*. To use the star-here.png icon you'll need to put it in your current icon theme's folder and backup+remove any icons that are named start-here.svg/png. Your icon theme should be located in */home/<username>/.icons/*.

Could you explain what you mean with the *top bars of windows* and what is wrong with it?

---

