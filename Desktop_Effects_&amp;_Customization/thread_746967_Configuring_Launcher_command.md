---
title: "Configuring Launcher command"
date: 2008-04-06
forum: Desktop Effects &amp; Customization
---

### Post by dingorunner on 2008-04-06
hello everyone, I think my question is a Yes/No question
I'm using gDesklet and I put a StarterBar on my desktop, I was wondering if I could change the Launchers' command-line so that they run on a terminal but instead of opening a new window terminal they would run on new tab on an existing terminal window,
Example:
I click on the Firefox Icon, a terminal window is opened and Firefox runs, then I click on some launcher Icon, a whole new terminal window is opened, what I want is that second launcher to run in a new TAB of the already opened terminal window instead of opening a whole new window.
Is that possible?

---

### Post by kaivalagi on 2008-04-06
Not sure, but looking at gnome-terminal help I found this:

```
  --tab                                           Open a new tab in the
                                                  last-opened window with the
                                                  default profile. More than
                                                  one of these options can be
                                                  provided.
```


It may be worth messing around with gnome-terminal parameters in your launcher?

---

