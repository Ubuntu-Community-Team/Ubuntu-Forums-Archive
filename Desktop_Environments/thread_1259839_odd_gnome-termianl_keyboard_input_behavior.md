---
title: "odd gnome-termianl keyboard input behavior"
date: 2009-09-06
forum: Desktop Environments
---

### Post by BattlePanic on 2009-09-06
I use Emacs and have recently started exploring the Org mode package included with Emacs.  This particular package offers a function which is bound to the keystroke Alt-Enter.  Unfortunately this keystroke doesn't seem to produce the desired results when using gnome-terminal.  I used the emacs-describe-key function to see what emacs was receiving when I hit Alt-Enter and it interprets the sequence as being Escape followed by Control-j.  I understand that emacs uses the alt key to mean escape, but why would the Enter key be interpreted and Control j?

As a test, I tried emacs under another virtual terminal, in this case rxvt-unicode and the keystroke was passed to emacs correctly.  emacs-describe-key reads Alt-Enter as Escape followed by Return, just as it should.

Can anyone fill me in on what is happening here and why.  Is it possible to change the behaviour of gnome-terminal to read this keystroke properly?

---

