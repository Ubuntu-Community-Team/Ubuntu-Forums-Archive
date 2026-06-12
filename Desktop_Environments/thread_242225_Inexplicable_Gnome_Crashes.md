---
title: "Inexplicable Gnome Crashes"
date: 2006-08-23
forum: Desktop Environments
---

### Post by mejy on 2006-08-23
Unfortunately I have just set up gnome on this machine, so it's difficult to tell what's caused it.  When launching gnome from GDM (normal or failsafe), everything hangs compeltely.

I cannot switch to any of the virtual terminals, and nothing responds.

If I go straight to a virtual terminal on startup, 'sudo killall GDM' and then 'startx', all virtual terminals become garbled and unreadable, although I can still switch between them.

What puzzles me, however, is that taking the following steps does not result in a crash:

    failsafe terminal
    gnome-terminal
    (new tab)
    metacity
    (new-tab)
    gnome-panel
    (new-tab)
    nautilus
    (new-tab)

If I then go to system->preferences->themes (just opening the dialogue is enough), I get the icons, metacity and GTK themes set for the account, so it's nothing wrong with these either.

What puzzles me is how Gnome can be so completely broken and yet all of it's core components seem to work fine.  Any thoughts on what else to try?

---

### Post by mejy on 2006-08-23
Well, after posting that I removed automatix and ssh (the two most recently installed programs, neither having been used), and now everythings works fine!

---

