---
title: "Add keyboard input source from CLI"
date: 2013-10-25
forum: Desktop Environments
---

### Post by antonvesnin on 2013-10-25
Hi all.

After upgrading to 13.10 it looks like we have no more deal with XKB for layout settings and input language switching, so I have a question.

Some times I need to add one ore two more input languages and remove them after little time. It's frequently operation, and in the pas there was a way to make it simple, like:

```
setxkbmap -layout "us,ru,de"
```
 So I was able to bind such command to hotkeys and add or remove needed language very fast and easy.

for now **setxkbmap** no affect laout at all, so what can I do?

I tryed to do something like:

```
 gsettings set org.gnome.desktop.input-sources sources "[('xkb', 'us'), ('xkb', 'ru'), ('xkb', 'ar')]"
```

And it really added layout to keyboard-indicator, but wan't change the input at all, so if I open GUI settings tool, i wan't find there new language.

I tryed also to do:
```
gsettings set org.gnome.libgnomekbd.keyboard layouts "['us', 'ru', 'de']"
```

But that have no effect at all.

diff between **gsettings list-recursively** before adding new layout from gui and after that isn't showing any difference except in  **org.gnome.desktop.input-sources sources**, diff between **gconftool-2 --recursive-list ** before and after insn't showing any differences at all.

So, **how can I add or remove input source and layout by console command**?

---

### Post by antonvesnin on 2013-10-26
Anyone?

---

