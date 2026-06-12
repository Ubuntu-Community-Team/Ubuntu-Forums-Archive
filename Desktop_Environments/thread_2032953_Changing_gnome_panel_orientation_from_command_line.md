---
title: "Changing gnome panel orientation from command line"
date: 2012-07-25
forum: Desktop Environments
---

### Post by grekhss on 2012-07-25
Hello to everyone!
I would like to change the orientation of the panel with task list. From command line.
I tried to use dconf and this is the result:
```
> dconf write /org/gnome/gnome-panel/layout/toplevels/bottom-panel/orientation top
error: 0-3:unknown keyword

Usage:
  dconf write KEY VALUE

Write a new value to a key

Arguments:
  KEY       A key path (starting, but not ending with '/')
  VALUE     The value to write (in GVariant format)

```
Writing a number to key 'orientation' (e.g. zero) gives the desired result - panel becomes at top. However I also want to orient it at bottom and writing numbers does not give any results. (I guess that positioning at top is just a reaction to the wrong key value.)
So, what I want is to change the orientation of the panel from command line. The choice of the command line is dictated by necessity to run this action automatically on startup.

Initially the problem has grown from the following: I have used to set two panels at bottom; panel with quick launch should be above the panel with task list. However, after reboot my manual changes partially disappear: both panels are at bottom, however, quick-launch-panel is under the task-list-panel. If manually set task-list-panel at top and then at bottom - everything is ok. If someone knows how to freeze the position of panels when they are both at bottom - this also will solve my problem. =)
Kind regards,
Sergey.

---

