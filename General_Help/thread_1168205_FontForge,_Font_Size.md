---
title: "FontForge, Font Size"
date: 2009-05-23
forum: General Help
---

### Post by gunksta on 2009-05-23
I've installed fontforge on my girlfriend's computer and she is reading the documentation to learn how to use it, but we have one problem, the font size in fontforge. (The irony of this problem is incredible.)

Looking at the dependencies, it looks like fontforge may use X directly. It clearly doesn't use GTK/QT/etc. For the monitor this is going to be used on, it is useful to increase the font size, which we have done for all of the GTK/QT apps installed on the system.

How can increase the size of the font used in the menus, dialog boxes, etc without affecting the rest of the fonts? I'm afraid if I use xorg's direct settings, I'll muddle the settings for GTK.

Thoughts?

---

### Post by Winge on 2009-07-17
This reply comes a bit late, but maybe it will be helpful to someone. The answer how to change the font size can be found here: [http://fontforge.sourceforge.net/faq.html#fontsize](http://fontforge.sourceforge.net/faq.html#fontsize) In short, edit ~/.Xdefaults and add a line such as

Gdraw.ScreenWidthInches: 14.7

Then run

xrdb ~/.Xdefaults

to update your settings.

---

