---
title: "Sloppy focus.  Can i turn off click raises?"
date: 2006-01-10
forum: Desktop Environments
---

### Post by jacobfe on 2006-01-10
I have been looking for the option to change to a completely sloppy focus.  I was able to do it with gnome 2.10 in debian but the option does not seem to be in the gnome with ubuntu.  There is a sloppy focus but is there a way to prevent windows clicked on from raising?  I want a true sloppy focus with no click to raise.

J

---

### Post by Voket on 2006-11-03
This is an old thread, but I'll finish it for completeness. (I read this thread trying to do the same thing, so maybe this will help someone).

Yes, you can.

1. Go into gnome configuration editor (type gconf-editor in terminal if you don't have a shortcut)
2. In the editor, go to: / -> apps -> metacity -> general
3. Uncheck the box next to "raise_on_click" (scroll down a little to see)

---

