---
title: "Mouse issues"
date: 2007-03-28
forum: Desktop Environments
---

### Post by kzip on 2007-03-28
I've run into a small problem with the mouse that I'm struggling to find info on how to resolve. The left click on my mouse only works if I hold down CTRL on the keyboard. It's a fairly standard two button MS PS/2 mouse. 

It was working ok originally, the problem started after I installed the 915resolution package and ran "dkpg-reconfigure xserver-xorg" so that I could get my monitor running at 1280x1024. I've tried re-running this command and choosing different options for the mouse, but I always get the same result.

Any ideas?

---

### Post by kzip on 2007-03-28
Turns out this wasn't an issue with xorg.conf but something screwy in my user profile. I deleted my home directory (it was a newish install, so nothing in it really) and restarted and it works fine now.

---

