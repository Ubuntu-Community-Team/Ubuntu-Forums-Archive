---
title: "how to remap ALT+i,j,k,l to arrow keys"
date: 2011-05-18
forum: Desktop Environments
---

### Post by mojones on 2011-05-18
I am running ubuntu 11.04 and I want to remap my keyboard so that pressing alt + i, j, k or l is the same as pressing an arrow key, i.e.

ALT+j = left
ALT+l = right
ALT+k = down
ALT+i = up

I have played around with xbindkeys to no avail, so if anybody has step-by-step instructions I would be very grateful.

---

### Post by Krytarik on 2011-05-18
It's not possible to use Alt as a modifier for keys, besides that that would conflict with the menu accelerators.

But it's possible to use AltGr for that, of course.

If you want to do that:

Create a file called ".Xmodmap" at the toplevel of your home directory, with those content:

~/.Xmodmap:```

keycode 31 = i I i I Up
keycode 44 = j J j J Left
keycode 45 = k K k K Right
# keycode 46 = l L l L 
keycode 58 = m M m M Down
```I guess you mean "m" for down, not "l". Otherwise, just modify the entries.

The next time you login, you will most probably be asked if you want to    use the newly created Xmodmap file*, then just choose "Add" and  confirm  with "OK".

*depends on if you had such a file before, and did already confirm/disable those query

Greetings.

---

### Post by mojones on 2011-05-19
Many thanks for the reply. I will give it a try using Alt Gr and see how that works out.

---

