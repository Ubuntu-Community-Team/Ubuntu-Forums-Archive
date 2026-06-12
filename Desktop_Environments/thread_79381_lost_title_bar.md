---
title: "lost title bar"
date: 2005-10-20
forum: Desktop Environments
---

### Post by spaznrq on 2005-10-20
It seems that I have lost my title bar (or maybe something else that I cannot see), so now I cannot move any of the windows that I open, and the only way to close the windows is by going File->Close or Quit.

It happened when I logged on one day and accidentally opened multiple Firefox windows in a split second.  I attempted to close them, but I hit the keys too fast (I used F1 to close windows as a keyboard shortcut) and suddenly my title bars disappeared and Help windows popped up.  I logged out and back in, but my title bars are still missing (probably because I automatically Saved Session when I log out, so it saved the mistake I made to make the title bars disappear).

What went wrong here?

---

### Post by darkmatter on 2005-10-20
Open a terminal and execute the command
```
metacity
```
to restart the window manager. Leave the terminal open for the moment and make sure that Under System -> Preferences -> Sessions -> Current Session, metacity is set to an Order of 20 and that the Style is set to restart. Close the terminal, metacity should exit and then restart.

Log out, choosing to 'Save current setup'. The next time you login, things should be back to normal

---

### Post by spaznrq on 2005-10-20
Thanks!  It worked.

Just to follow up, what is metacity?  And what did I do to screw it up in the first place?

---

### Post by SilentCacophony on 2005-10-20
Hi. Metacity is the Window Manager for the Gnome Desktop. It handles drawing the titlebar, borders, and widgets around windows, among other things.

It probably just crashed because of the flood of opening windows you mentioned in your post.

---

### Post by pixxelle on 2005-10-25
Thanks to *darkmatter's* post in this thread, I finally was able to fix the no- titlebar/no window borders GUI problem in one of my user accounts I trashed while trying out Gnome themes a month ago.

It was one baby step at a time (...and I had finally figured out it was a metacity problem,  what to do?), but a good learning experience.

Thanks so much for the helpful post...:D

---

### Post by chinese_ys on 2007-08-14
but if I want to remove the title bar of gnome-terminal only, what can i DO?

Thanks!

---

