---
title: "Print Screen infinite loop"
date: 2009-03-22
forum: General Help
---

### Post by breem42 on 2009-03-22
I recently encountered a problem with the print screen button under
kubuntu (hardy).  Apparently this is a problem for Gnome too.  I thought
I'd share the solution I found on [[COLOR="Blue"]launchpad[/COLOR]]("https://bugs.launchpad.net/ubuntu").

On my keyboard, the Print Screen button is not far from the backspace
button.  Consequently, I occasionally pressed the Print Screen button
rapidly when I was trying to delete a bunch of text.

This resulted in an "infinite loop" where 'snapshot' windows popped up
over and over again making the computer unusable, and forcing me to do a
hard reboot.

It took some time to find the [[COLOR="Blue"]solution[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/84278").

What worked for me was to open a terminal window and type the following

```
[FONT="Courier New"]xset -r 111[/FONT]
```

This turns off the 'repeat' functionality for the 'Print Screen' key.
Apparently the keycode for that key is 111.  If you have a different
keyboard the keycode needed may be different.

Now if I accidentally hit the 'Print Screen' button, I only get one
'snapshot' window for each keypress, which is the correct functionality.
This is not a 'real' fix, just a workaround, but it is pretty good.  It seems
good enough to that it would make a good permanent and default
setting.

---

