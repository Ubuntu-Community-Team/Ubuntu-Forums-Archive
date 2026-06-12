---
title: "wrong font in emacs"
date: 2007-12-14
forum: Desktop Environments
---

### Post by Cowloon on 2007-12-14
After upgrading to gutsy from edgy (and briefly, feisty), the font 10x20 in emacs displays as what looks like the Sony fixed-width font. I select the font either by passing -fn on the command line, or by specifying it as an X resource, and get the sonyish font.

In /usr/share/X11/fonts/misc/fonts.alias 10x20 is:

-misc-fixed-medium-r-normal--20-200-75-75-c-100-iso8859-1

If I specify that font as an X resource, instead of 10x20, when starting emacs I get the font I'm used to.

What gives?

---

