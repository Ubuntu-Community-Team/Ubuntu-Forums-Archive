---
title: "Rhythmbox Opens on arrow keys"
date: 2010-01-24
forum: Desktop Environments
---

### Post by mohaakilla51 on 2010-01-24
Ok, so if my number lock is off, all the keys on my keyboard function properly (with the exception of the number pad not being numbers, obviously), but if I turn the num-lock on, then all the keys from print screen to pause and down to the arrow keys (ie: home, insert, delete, end, pgup, pgdown) attempt to open Rhythmbox when they are pressed. Any idea why this is happening?

---

### Post by 311005901 on 2010-01-24
Check what you've got under "System>Preferences>Keyboard Shortcuts".

---

### Post by 311005901 on 2010-01-26
Any updates on your issue? :)

---

### Post by kingdon on 2012-05-11
Reviving an old thread ...

Running Karmin 9.10

I just made some minor mods to my xorg.conf (dual monitors, swapped order). After X restart I'm experiencing same problem as OP. I've uninstalled rhythmbox and now get the message ...

Couldn't execute command: rhythmbox
Verify that this is a valid command.

... whenever num lock is on and I push any cursor keys, insert, home, page up, page down, end, delete, print screen. Interestingly, scroll lock or pause/break don't try to start rhythmbox.

In a terminal I did ...
```
xev | sed -n 's/^.*state \([0-9].*\), keycode *\([0-9]\+\) *\(.*\), .*$/keycode \2 = \3, state = \1/p'
```
... all the keys listed above give no response when I press them and num lock is on.

---

### Post by kingdon on 2012-05-11
Wow. I just noticed this is happening when I hold the shift key and used the cursor keys to select text, but with num lock off. This is crazy!

---

### Post by kingdon on 2012-05-11
Just found a solution in post # 23 and #24 of [HTML]http://ubuntuforums.org/showthread.php?t=193936&highlight=Couldn%27t+execute+command%3A+rhythmbox[/HTML]

I changed my keyboard shortcut for "Launch media player" to Ctrl+Mod4+Space and problem is solved.

---

### Post by kingdon on 2012-05-15
I just started my Windows XP virtual box, and the same thing is happening there ... with num lock on, home, insert, delete, end, pgup, pgdown open Windows Media Player.

---

