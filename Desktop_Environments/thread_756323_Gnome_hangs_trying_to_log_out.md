---
title: "Gnome hangs trying to log out"
date: 2008-04-15
forum: Desktop Environments
---

### Post by swtaarrs on 2008-04-15
Whenever I try to log out of Gnome by using either the button in the top right of the screen or the Quit item of the System menu, X stops responding to mouse and keyboard input for about 5 minutes before showing the shutdown/restart/etc... buttons.  It's not completely hung, my system monitor panel widget keeps going the whole time.  I'm using Hardy but this was also a problem in Gutsy.  Back in Gutsy it seemed to only happen when I had compiz on but now it happens nearly all the time.  When it does happen I usually just go over to a terminal and restart manually, but if I wait it out there aren't any hibernate or suspend buttons when the dialog finally comes up, so this might have something to do with acpi.  

If I create a new user and log into Gnome as him it works fine, so I'm guessing it's some configuration file in my home directory.  However, I've tried getting rid of .gnome*, .metacity, and .gconf* and it still happens.  Is there some other config/directory file I could be missing, or does anyone know what's going on?  I've also tried disabling the nvidia driver and that didn't help.

---

### Post by swtaarrs on 2008-04-15
I did a thorough search of the forums before posting that but I forgot to search bugs on Launchpad.  Anyway, I found out that the problem was that I had removed the power management daemon from my session startup list (since this is a desktop, not a laptop).  I added it back and now it's working fine.

---

### Post by b3nw on 2008-04-15
I was having a similar issue on hardy, but after a re-install (for other reasons) i'm not longer having it. Interesting to know why it was hanging up though.

---

### Post by brendan6 on 2008-04-16
If you had unchecked Gnome Power Manager from startup programs it causes gnome to hang when trying to close...something about it trying to end a process that didnt exist but was expected.

Anyways..simple fix, leave Gnome Power Manager on :P

---

