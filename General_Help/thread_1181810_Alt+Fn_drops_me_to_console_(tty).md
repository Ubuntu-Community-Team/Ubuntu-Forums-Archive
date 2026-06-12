---
title: "Alt+Fn drops me to console (tty)"
date: 2009-06-08
forum: General Help
---

### Post by Sam Stone on 2009-06-08
Hi all!

Please, help me with my problem ) When PC boots up and i logon on ubuntu goes to console when i press alt+f1 (or f2 etc) instead of menu, "run application", etc. After logout/logon  all works fine. So it isn't a user problem.

Linux jaunty-x64 2.6.28-11-generic x86_64 GNU/Linux

PS
Sorry for my english ^_^"

---

### Post by quixote on 2009-06-09
Maybe you have somehow acquired an unexpected keyboard shortcut on your system?  See what's under System -> Preferences -> keyboard shortcuts.  Some way down under "Desktop" there's the option to have a shortcut for "run a terminal".  Way at the bottom it's also possible to define custom shortcuts, and maybe there's something down there.

Be nice if it was this simple.  :)

---

### Post by Sam Stone on 2009-06-10
It's too easy :)
alt+f1 - show the panel's main menu
alt+f2 - show the panel's "Run Application" dialog box

And why it disables after relogin?.. >_<

---

### Post by quixote on 2009-06-10
Are you saying that those are the shortcuts listed under the keyboard shortcuts?  But that alt+f1 gives you a terminal window anyway?

Strange.

---

### Post by Sam Stone on 2009-06-11
One thing which I have forgotten: when I come back in a gui, I have "Run Application" opened (if I pressed alt+f2 before).
Maybe it's a bug with ctrl key?..

---

### Post by quixote on 2009-06-11
As I said, strange.  I doubt it's a bug in the ctrl key because then presumably you'd get weird behavior in other situations too.  It seems to me that some gnome setting (or maybe X ??) has gone blooie, but I don't know enough about the guts of either one to have any suggestions.

Can you explicitly set the key combinations for the behavior you expect in Keyboard Shortcuts?  I know it should be the default, but set it anyway, if you can.  Maybe that would override whatever is cauing the strange behavior?

---

