---
title: "Backspace not working in screen"
date: 2006-07-09
forum: Desktop Environments
---

### Post by Arrigi on 2006-07-09
A few days of using xubuntu 6.06 resulted in the backspace key not working anymore in screen.. which is quite annoying. I didn't change anything to the screen configuration (if there is one) BEFORE that ocurred. Later I've been reinstalling screen and deleted .screenrc (although that didn't seem to make a difference). I do seem to have that file back (created by screen?).

How can I make my backspace key work again?
Thanks for you help!

---

### Post by Arrigi on 2006-07-09
OK..
Looks like it was a setting in gnome-terminal (it DID work in xterm/other tty). The behavior of the backspace key had to be set to ^H instead of "auto" .. I wonder why it did work the first few days!

---

