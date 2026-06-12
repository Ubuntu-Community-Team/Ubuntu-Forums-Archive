---
title: "Make multimedia keyboard key start galculator instead of gcalctool?"
date: 2005-12-13
forum: Desktop Environments
---

### Post by ubuntuuser on 2005-12-13
Hi! I have a Microsoft keyboard with a lot of those fancy additional keys on it. I have for example a little button to start the calculator. When I push the key the program that starts is Gcalctool. But I want to use galculator instead. Now, where can I change this?

Thanks in advance.

---

### Post by aysiu on 2005-12-14
This may not be the answer you're looking for, and it may not even work, but since no one's answered you in 11 hours, it's worth a shot, right?

Find out what the funky name is for the Calculator multimedia key. For example, mine is 0xa1. Go to System > Preferences > Keyboard Shortcuts and disable the keyboard shortcut for Calculator.

Then, go to Applications > System Tools > Configuration Editor > Apps > Metacity > Global Keybindings /Keybinding Commands

Make the Global Keybinding 0xa1 (or whatever your multimedia key is) and make the corresponding keybinding command ```
galculator
```

---

### Post by ubuntuuser on 2005-12-14
Thanks. I have found a kind of dirty workaround. I always use galculator, so I backed up the original /usr/bin/gcalctool and then copied /usr/bin/galculator to /usr/bin/gcalctool.
Not very clean, but does what I expect it to do.

---

### Post by aysiu on 2005-12-14
[QUOTE=ubuntuuser]Thanks. I have found a kind of dirty workaround. I always use galculator, so I backed up the original /usr/bin/gcalctool and then copied /usr/bin/galculator to /usr/bin/gcalctool.
Not very clean, but does what I expect it to do.[/QUOTE] That was going to be my second suggestion... Glad it all worked out, however "dirty" the solution was.

---

