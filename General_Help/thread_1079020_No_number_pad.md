---
title: "No number pad"
date: 2009-02-23
forum: General Help
---

### Post by NoBugs! on 2009-02-23
My keyboard does not have a number pad. Is there a way I can assign a key to "num-lock" and make this num-lock turn part of the keyboard into a num-pad? Perhaps these keys:
789
uio
jkl
m
could be turned into:
789
456
123
0
I think this would really be helpful.
Thanks

---

### Post by mb_webguy on 2009-02-24
I don't know that you can do *exactly* what you want, as far as a Num Lock key, but you could use xbindkeys to create key combos that will do what you want.  For example, the keys you mention could do what you want while you're holding down the Shift+Super keys (or any other meta keys).  Just make sure you're not duplicating an existing key combo.

Here's a [how-to on remapping keys]("http://ubuntuforums.org/showthread.php?t=623078").  It's not exactly what you're talking about, but it should put you on the right track.

---

### Post by NoBugs! on 2009-06-05
"numlockx toggle" command can enable/disable the numlock, it turns the letter keys to numbers. However, the letter and arrow keys won't work when the num lock is activated, and I can't seem to remap a key to numlock key. For now I just setup a shortcut to "numlockx toggle".

---

### Post by NoBugs! on 2010-06-15
I found how to set up the num-lock if you don't have a num-lock button:
Go to System-Prefs-Keyboard Shortcuts
In the Custom section, add "numlock", shortcut to "numlockx toggle"
and set it to an unused function key

---

