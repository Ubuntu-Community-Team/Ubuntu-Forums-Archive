---
title: "Upgrade to 8.04 breaks keyboard repeat"
date: 2008-10-01
forum: Desktop Environments
---

### Post by Cracauer on 2008-10-01
I upgraded from 6.06 to 8.04.

Worked nicely, but I don't get any key repeat in X11. I use 
Option  "XkbDisable"
because the XKBD extension breaks a number of other things for me. I am running with XKBD off for 10+ years and I always got key repeat inherited from the keyboard setting in the console.

In fact, right now Alt-F2 switching to the text console sees working key repeat as it should. Just the new Xorg somehow manages to kill it. Has nothing to do with GNOME, it also happens without GNOME. The login window is already affected.

"xset q" shows repeat on and the same bitmap as on the working installations.

One working machine also uses xorg-7.3. That machine is running Debian lenny/sid. I also have Xorg-7.3 on a FreeBSD installation with no problems.

For now I have to conclude that Ubuntu broke this somewhere between Debian and Ubuntu. Is there an easy way to see the diff between your packages and Debian's original?

(note that this seems to be the opposite problem of some unwanted key repeat I see reported, maybe you did a fix that went bad?)

Thanks
Martin

---

### Post by Cracauer on 2008-10-01
Hmmm, OK I'm sorry, I think it's a xorg-7.3 issue after all.

Although I had blindly assumed that my other 7.3 machines (Debian and FreeBSD) work fine with KBDdisable, they actually don't. Normally I always turn this off first thing on a new machine, but not in this case. I don't need the things that KBD breaks on these installations, so I didn't notice.

I think I should go off discuss this with the Xorg folks.

I assume it's highly nontrivial to run 7.2 on Ubuntu 8.04, right? There's no direct support for mixing releases like in Debian?

---

