---
title: "UK Keyboard layout - Pound symbol is a J?"
date: 2010-11-28
forum: Desktop Environments
---

### Post by Confused_Cheese on 2010-11-28
I've set my keyboard layout to UK, but for some reason shift + 3 is J rather than the pound/sterling symbol. Flicking through all layouts, shift + 3 is always J for UK layouts.

Any ideas? Using xmodmap I can change it for the current session, but it doesn't seem to stick no matter what I try :(

---

### Post by tom4everitt on 2010-11-29
Using xmodmap should work. 

Put the xmodmap commands in a file

~/.Xmodmap

and the next time you log in, you should be asked whether to always load that file.

---

