---
title: "Launch focus"
date: 2007-08-24
forum: Desktop Environments
---

### Post by earther on 2007-08-24
This is too weird.

When I open a text file in Nautilus, gedit pops up in front and takes focus like it should.  

However, when I open an html file in Nautilus, Firefox stays in the background.  I have checked preferences and config files but can't see how to get Firefox to take focus in the foreground when I open an html file from Nautilus.

What am I missing?

(Using Feisty, Gnome and no Beryl)

---

### Post by earther on 2007-08-27
*** Bump ***

---

### Post by Wolki on 2007-08-27
Do you interact with the nautilus window in any way after launching the html file? That may cause the focus stealing prevention to take effect, ie the windowmanager assumes you're using nautilus right now and don't want the firefox window to interrupt what you're doing.

If that's not it I don't know :-/

Oh, do you already have firefox open when opening the file?

---

### Post by earther on 2007-08-27
No and no unless you consider clicking to lauch "interacting".

---

### Post by Wolki on 2007-08-27
no, clicking to lauch shouldn't trigger the focus-stealing prevention. Then I don't have a clue :-/

---

