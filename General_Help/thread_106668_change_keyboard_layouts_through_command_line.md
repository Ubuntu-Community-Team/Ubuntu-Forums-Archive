---
title: "change keyboard layouts through command line"
date: 2005-12-21
forum: General Help
---

### Post by h.mehdi on 2005-12-21
Hi Friends,

I'm looking  for a way to add a new layout (language) and then change layout options through command line, can any one please help ?

---

### Post by ace2005 on 2005-12-21
Well the command is "setxkbmap", have a look at "man setxkbmap" for more info

What do you want to change it to?

---

### Post by ace2005 on 2005-12-21
Well the file "/usr/X11R6/lib/X11/xkb/rules/xorg.lst" has a list of layouts you can use

Here is a few lines:
  pc101           Generic 101-key PC
  pc102           Generic 102-key (Intl) PC
  pc104           Generic 104-key PC
  pc105           Generic 105-key (Intl) PC

Hope this helps

---

### Post by h.mehdi on 2005-12-21
Thanks for reply,
Can you please have a look at this page: [http://www.hezardastan.org/breezy_persian_support/](http://www.hezardastan.org/breezy_persian_support/)
I would like to do this KB layout adding and changing the layout options and adding the KB indicator to the above panel by command line...

---

### Post by ace2005 on 2005-12-21
Why can't you go into gnome and change it, it looks pritty streight forward to me,

"setxkbmap us" changes the keyboard mapping to us format for me, i use KDE not sure about gnome

---

