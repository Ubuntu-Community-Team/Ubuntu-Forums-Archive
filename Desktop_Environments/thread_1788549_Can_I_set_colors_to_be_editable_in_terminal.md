---
title: "Can I set colors to be editable in terminal?"
date: 2011-06-22
forum: Desktop Environments
---

### Post by Twisted871 on 2011-06-22
Hey all,

I am trying to use the [ncurses]("http://en.wikipedia.org/wiki/Ncurses") library for a little side project and am currently trying to display text with varying colors on the screen. I would like for my program to be able to change the hues of the default colors(e.g. make red a little dark, blue a little lighter, etc).

However, according to the ncurses function [can_change_color()]("http://linux.die.net/man/3/has_colors") my terminal does not allow for colors to be altered. I know how to change the palette of colors that my terminal is using but I was wondering if there was a way to allow my colors to be "editable" in a sense. 

My terminal is Gnome 2.30.2 and I'm running Ubuntu 10.04LTS, thanks for any help!

---

### Post by itcotbtoemik on 2011-06-23
ncurses looks at the terminal entry, using $TERM to select that.  gnome-terminal hardcodes $TERM to "xterm" (bug). The "xterm" entry doesn't have the feature that ncurses is looking for (initc), since "xterm" applies to the 8-color configuration (technically it could, but that's a different matter).

The feature is part of the xterm-88color or xterm-256color entries because it's closely associated with the capabilities for setting colors.

Actually gnome-terminal should use one of the "vte" or "gnome" entries, but none of those specify initc since vte's support for xterm's 256-color palette has been erratic.  You can probably get the effect you're looking for by setting TERM=xterm-256color.

---

### Post by Twisted871 on 2011-07-28
Sorry it took me a month to reply....

Yes itcotbtoemik, that did work. Thank you very much for the help.

---

