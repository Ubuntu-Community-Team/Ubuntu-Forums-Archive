---
title: "Windows manager crashed?"
date: 2006-01-03
forum: General Help
---

### Post by pbb on 2006-01-03
I am just a newbie, so things may not be as bad as they seem to be now.

I was just browsing around with Firefox, when all of a sudden the screen started flickering. Afterwards, all my windows had lost their border and titlebar, only the window-contents was visible anymore.

I tried restarting the computer, but the problems persists. All windows now open up in the upper left corner of the screen, and without any titlebars I cannot move them around.

I tried going to System > Preferences > Windows, and I get the following error message:

```
Cannot start the preferences application for your window manager

Window manager "unknown" has not registered a configuration tool
```

What should I do to fix things??

---

### Post by pbb on 2006-01-03
Okay, I found the solution.

1. Run "metacity &" in a terminal.
2. Log out with "Save current setup" checked.

Thanks anyway!

---

